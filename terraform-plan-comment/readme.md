# terraform-plan-comment
This action will create a github comment on a pull request given information from terraform plan

## Inputs
| input             | required              | description                                                                               |
| ----------------- | :-------------------: | ----------------------------------------------------------------------------------------- |
| github_token      | :heavy_check_mark:    | The github secret to use to create a comment, usually this is `secrets.GITHUB_SECRET`     |
| plan_output       |                       | The standard **output** of the plan step to include in the comment.                       |
| plan_outcome      |                       | The **outcome** of the plan step. This is usually SUCESS OR FAILED                        |
| format_outcome    |                       | The **outcome** of the format step.                                                       |
| init_outcome      |                       | The **outcome** of the init step.                                                         |
| validate_outcome  |                       | The **outcome** of the validate step.                                                     |
| validate_output   |                       | The **output** of the validate step.                                                      |