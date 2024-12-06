# CS781-Project
Link to GitHub repository: [https://github.com/adityanemiwal/CS781-Project](https://github.com/adityanemiwal/CS781-Project)

### Running Instructions
Setup [Tempest_in_Action](https://tempest-synthesis.org/shieldedrl/docker/index.html) using Docker.

Place the [jupyter notebook](shieldSynthesis.ipynb) from the repository in the /opt/notebooks directory in the docker container.<br>
Place the [Playground.py](Playground.py) from the repository at `/opt/environments/notebooks/Minigrid/minigrid/envs/Playground.py` in the container.

Run the notebook

### Customisations 
The second cell in [notebook](shieldSynthesis.ipynb) (under the heading "Load MiniGrid Environment") defines n, k, and defines the minigrid environment to be used.

`n`, `k` can be updated as desirable. Notes:
- Keep `k` as 1 or 2. `k=0` doesn't add any new information, and `k>=3` might take too much time to render and potentially crash the kernel
- For the given playground, (`n=5`,`k=2`) is tested. But for larger grids, or larger `n` (>10), the notebook may take longer
- Shield are visualised for specific cases:
  - `k=0`
  - `k=1` and `n>=4`
  - `k=2` and `n>=5`

To use custom environment, update the `/opt/environments/notebooks/Minigrid/minigrid/envs/Playground.py` file accordingly.

### Outputs
A `test/` directory is created, in which the `PRISM` for updated MDP is exported.
The new shield is also exported to `test/`

### Interaction
The last cell of the notebook is there for interaction with the environment using the new shield.

A string `observe_sequence`, consisting of `'a'`s and `'b'`s should be initialised. 

The length of the string is the length of simulation.<br>
`'a'` at index `i` represents that output after `i`<sup>th</sup> action will be observed.<br>
`'b'` at index `i` represents that output after `i`<sup>th</sup> action will not be observed.

Ensure that the sequence has at most `k` `'b'`s in any contiguous substring of length `n`.<br>
Otherwise, an error might be thrown.

The cell outputs the state of the environment and allowed actions before asking for next action as input.<br>
The cell then performs that action, and then according to whether it read `a` or `b` from the string, updates the state.<br>
The above steps go on `len(observe_sequence)` times

For information regarding what a state represents, please check the report.

# Creative Commons Attribution-NonCommercial-NoDerivatives (CC BY-NC-ND)

This code bears a license to permit others to **_share_** (mirror) your mod content, providing that they credit you and don't use your work for commercial purposes.

You can view additional details on [this page](https://creativecommons.org/licenses/by-nc-nd/4.0/)


