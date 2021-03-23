
#Demo
To demonstrate vulnerabilties, add a known package like the following.

    "msgpack5": "5.2.0"

to package.json

You can find more vulerabilties to validate here [https://www.npmjs.com/advisories](https://www.npmjs.com/advisories)

Note msgpack5 is fixed in 5.2.1 so you can update, push the fix and test the CI workflow.

You can view produced files online in the uploaded files section for the actions.
There will be two files `crda.json` and the converted `crda.sarif`

You can view the sarif file in many ways

1. Github Security Tab.

2. The VSCode Plugin [https://marketplace.visualstudio.com/items?itemName=MS-SarifVSCode.sarif-viewer](https://marketplace.visualstudio.com/items?itemName=MS-SarifVSCode.sarif-viewer)

3. A web based viewer  [https://microsoft.github.io/sarif-web-component/](https://microsoft.github.io/sarif-web-component/)

 

