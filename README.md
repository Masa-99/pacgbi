# Pipeline for Automated Code Generation from Backlog Items

The Pipeline for Automated Code Generation from Backlog Items (PACGBI) uses a Large Language Model (LLM) to automatically implement backlog items through a GitLab CI pipeline.

## Features

- Automated implementation of backlogitem in under 9 minutes
- Seamless integration with GitLab CI/CD
- Flexiblity to use any OpenAI model

## Setup

1. Copy the content of the `.pacgbi.yaml` into the `.gitlab-ci.yaml` of the GitLab project where you want to use the PACGBI.
2. In the GitLab project, create a GitLab Access Token as described in this [GitLab article](https://docs.gitlab.com/ee/user/project/settings/project_access_tokens.html#create-a-project-access-token).
    > **_NOTE:_**  Use a meaningful name to distinguish the PACGBI-generated code and merge request from your developers'. 
    
    Save the token key and value for the next step.
3. Next, go to **Setting > CI/CD > Variables** and declare the following variables:

| Key | Value | Visibility (optional) | Protected |
| --- | --- | --- | --- |
| GITLAB_ACCESS_TOKEN | << Your GitLab access token from Step 2 >> | No | No |
| OPENAI_API_KEY | << Your OpenAI API Key >> | No | No |
| OPENAI_MODEL | << Name of the OpenAI model you want to use >> | No | No |
| OPENAI_SYSTEM_MESSAGE | << Your individual system message >> | Yes | No |

The OpenAI API key can be found and created [here](https://platform.openai.com/api-keys). A list of current OpenAI models is shown [here](https://platform.openai.com/docs/models). We recommend using the newest model.

> **_NOTE:_** Ensure you have sufficient OpenAI credits to use the PACGBI.

In our work, the system message was: 
>As a senior developer on a web development team, you are responsible for developing a payment frontend application. It is important to regenerate the entire code file each time, without providing explanations for the code.

4. To operate GitLab CI/CD and get the PACGBI running, a GitLab runner must be configurated in **Setting > CI/CD > Runners**, as shown in this [GitLab article](https://docs.gitlab.com/runner/).

Now, everything is set up for usage.

## Usage:

1. Open the GitLab Issue that you want to be implemented by the PACGBI.
2. Set an Issue label with the name of the code file which needs to be modified by the PACGBI to solve the Issue (without file extension, only .tsx files are currently supported).
> **_NOTE:_** Currently, the PACGBI only supports modifying Issues with **one** file aka one label.
4. Make sure the Issue description is **clear** and **detailed**. In our paper, which is based software development in a Scrum team, we used this template:

> Benefit Hypothesis: << Your text here >>
>
> Story Context: << Your text here >>
>
> Technical Solution: << Your text here >>
>
> Acceptance Criteria: << Your text here >>`
5. Create a new branch with the prefix **“bot/<< name of the branch >>”** to trigger the PACGBI.
6. You can observe the pipeline process in **Build > Pipelines**. If the pipeline runs through all stages successfully, you can find the merge request with the LLM-generated code in **Code > Merge requests**.
> **CAUTION:** The generated merge request should always be reviewed by developers before merging into the main code base to avoid unexpected and unintentional changes!

## Paper

We researched the capabilities of the PACGBI and LLM-based code generation in a case study on React front end development in our research paper: "Potentials and Limitations of LLM-based CI/CD pipelines". There you can gain more insights about its impact on code quality, costs and acceptance rate.

Further, we wrote a tool demonstration paper: "PACGBI: Pipeline for Automated Code Generation from Backlog Items".

A demonstration of the tool including a screencast is available on [Youtube](https://youtu.be/TI53m-fIoyc).

## License

GNU GPLv3
