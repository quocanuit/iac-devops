# Guideline
1. Create bucket then upload [cfn_nested_templates](./infras/aws/cfn_nested_templates/)
![](./docs/assets/g1.png)
2. Use **Deploy to CloudFormation** template
![](./docs/assets/g2.png)
3. Use CodeConnection **Connect to Github**
![](./docs/assets/g3.png)
4. A CloudFormation Starter Template will be deployed
![](./docs/assets/g4.png)
5. Edit the Pipeline, add new stage for CodeBuild
![](./docs/assets/g5.png)
6. Hit **Create project**
![](./docs/assets/g6.png)
7. **Use a buildspec file**. Leave other options as default.
![](./docs/assets/g7.png)
8. Done
![](./docs/assets/g8.png)
9. In **Edit: Triggers**, make sure it got a branch in "Include branches"
![](./docs/assets/g9.png)
10. Modify **buildspec.yml** bucket name
![](./docs/assets/g10.png)
11. Modify **.taskcat.yml** TemplateBucketName and KeyName
![](./docs/assets/g11.png)
12. Modify **main-cfn.yaml** TemplateBucketName and KeyName (and other parameters if needed)
![](./docs/assets/g12.png)
13. Commit changes
![](./docs/assets/g13.png)
14. Then the pipeline will automatically be triggered, then got some permission errors. To resolve them, create new inline policy for your CodePipeline service role. ([cp_inline_policy](./infras/aws/code_pipeline/cp_inline_policy.json))
![](./docs/assets/g14.png)
15. Also create new inline policy for CodeBuild service role. ([cb_inline_policy](./infras/aws/code_build/cb_inline_policy.json))
![](./docs/assets/g15.png)
16. Retry stage and it should run successfully.
![](./docs/assets/g16.png)