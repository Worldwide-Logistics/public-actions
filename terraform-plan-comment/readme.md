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

## Example Usage
```yaml
steps:
    # previous steps
  - name: Run Terraform Plan
    id: plan
    run: terraform plan -no-color -input=false
    continue-on-error: true

  - name: Create Terraform Plan Comment
    uses: Worldwide-Logistics/public-actions/terraform-plan-comment@main
      with:
        # required
        github_token: ${{ secrets.GITHUB_TOKEN }}
        
        # If you only have the plan step
        plan_output: ${{ steps.plan.outputs.stdout }}
        plan_outcome: ${{ steps.plan.outcome }}

        # If you have have other steps
        format_outcome: ${{ steps.fmt.outcome }}
        init_outcome: ${{ steps.init.outcome }}
        validate_outcome: ${{ steps.validate.outcome }}
        validate_output: ${{ steps.validate.outputs.stdout }}
```