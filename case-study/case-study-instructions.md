# Instructions for case study

If you want to try out the pipeline you can follow these steps to reproduce the case study that was performed for research.

1. Fork the [cypress-realworld-app](https://github.com/cypress-io/cypress-realworld-app) repository and transfer it into your GitLab account.
2. Create an GitLab Issue for each backlog item in the [Product Backlog](Product_Backlog.pdf) based on this structure:
   
| GitLab Issue   | Product Backlog Item            |
|----------------|---------------------------------|
| Name       | Title                                     |
| Description| Description                               |
| Labels     | Create a new label for each file mentioned in the Product Backlog Item Description |

4. Configure PACGBI as described in the [Setup](/README.md).
5. Create a new branch for each backlog item. If configured right, this should trigger PACGBI eight times.
6. As described in the paper, all pipelines run through successfully. When inspecting the merge requests in detail, three are implemented in an acceptable review-for-review state.
