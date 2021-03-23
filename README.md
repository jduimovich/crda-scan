# Code Ready Dependency Analytics to Sarif demo

This demonstrates the use of the CRDA CLI to scan the package.json file for vulnerabilities and upload to the github code-ql security service.

The CRDA CLI outputs a json payload and this demo uses a github action to converts the CRDA format to SARIF so it can be used with code-ql. 
 
The file includes two known security issues to enable the demo.
The repository only includes the package.json file and is not executable to prevent usage of the demo itself which specifically includes known vulnerabilty dependencies. 

You can find the [CRDA CLI here !](https://github.com/fabric8-analytics/cli-tools/releases/tag/v0.0.1) 

To use it, use `jduimovich/crda-sarif-poc@main` in a workflow, as per this yaml. This demo will only check checks package.json.
 
```
- name: Run CRDA and Convert to Sarif
        uses: jduimovich/crda-sarif-poc@main
        with:
          input-file-name: package.json
          snyk-token: ${{ secrets.SNYK_TOKEN }}
          output-file-name: output.sarif
```         

The result can be found in the security tab. 
          
![Issues Found](crda.png)

See the file workflow example here.
```
https://github.com/jduimovich/crda-scan/blob/main/.github/workflows/ci.yml
```

To test this, you can fork this repo, enable the workflow in the Github Actions tab and set a secret `SNYK_TOKEN`. You can do this in the Github UI or via the gh cmd line.
To get a snyk token, goto [snyk.io!](https://snyk.io/). 

```
gh secret set SNYK_TOKEN -b <your secret token> 
```

You can find more vulerabilties to validate here at [https://www.npmjs.com/advisories](https://www.npmjs.com/advisories)

# Demo
To demonstrate vulnerabilties, add a package with a known vulnerability to package.json. 

    "msgpack5": "5.2.0"


You can find more vulerabilties to validate here [https://www.npmjs.com/advisories](https://www.npmjs.com/advisories)

Note msgpack5 is fixed in 5.2.1 so you can update, push the fix and test the CI workflow after a fix.

You can view produced files online in the uploaded files section for the actions.

There will be two files `crda.json` and the converted `crda.sarif`

You can view the sarif file in many ways

1. Github Security Tab.

2. The VSCode Plugin [https://marketplace.visualstudio.com/items?itemName=MS-SarifVSCode.sarif-viewer](https://marketplace.visualstudio.com/items?itemName=MS-SarifVSCode.sarif-viewer)

3. A web based viewer  [https://microsoft.github.io/sarif-web-component/](https://microsoft.github.io/sarif-web-component/)

 

