Create a devcontainer.json
{
	"name": "Cruddur Config",

	// The optional 'workspaceFolder' property is the path VS Code should open by default when
	// connected. This is typically a file mount in .devcontainer/docker-compose.yml
	"workspaceFolder": "/workspaces/${localWorkspaceFolderBasename}",
	"features": {
		"ghcr.io/devcontainers/features/aws-cli:1": {}
	},
    //add extensions to your vscode 
	"customizations": {
		"vscode": {
			"extensions": [
				"ms-python.python",
				"ms-azuretools.vscode-docker",
				"mtxr.sqltools"
			]
		}
	},
    // run npm install inside frontend-react-js folder 
	"postCreateCommand": "cd /workspaces/aws-bootcamp-cruddur-2023/frontend-react-js && npm install"
}

Add lines to docker-compose.yml for it to work on Codespaces
backend-flask:
    environment:
        FRONTEND_URL: "https://${CODESPACE_NAME}-3000.${GITHUB_CODESPACES_PORT_FORWARDING_DOMAIN}"
        BACKEND_URL: "https://${CODESPACE_NAME}-4567.${GITHUB_CODESPACES_PORT_FORWARDING_DOMAIN}"

frontend-react-js:
    environment:
        REACT_APP_BACKEND_URL: "https://${CODESPACE_NAME}-4567.${GITHUB_CODESPACES_PORT_FORWARDING_DOMAIN}"