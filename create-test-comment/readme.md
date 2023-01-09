# create-test-comment
this action adds a comment to the current pull request showing test output

## Inputs
| input             | required              | description                                                                               |
| ----------------- | :-------------------: | ----------------------------------------------------------------------------------------- |
| github_token      | :heavy_check_mark:    | The github secret to use to create a comment, usually this is `secrets.GITHUB_SECRET`     |
| test_output       |                       | The standard **output** of the test step to include in the comment.                       |
| test_outcome      |                       | The **outcome** of the test step. This is usually SUCESS OR FAILED                        |

## Example Usage
```yaml
steps:
    # previous steps
  - name: run tests
    id: tests
    run: dotnet test
    continue-on-error: true

  - name: Create Terraform Plan Comment
    uses: Worldwide-Logistics/public-actions/create-test-comment@main
      with:
        # required
        github_token: ${{ secrets.GITHUB_TOKEN }}
        test_output: ${{ steps.tests.outputs.stdout }}
        test_outcome: ${{ steps.tests.outcome }}
```