# composite-actions
What is a composite action?
A composite action allows you to combine multiple workflow run steps within one action. You can bundle together multiple run commands into a single action and reduce duplication in your worklow.

# How to use composite actions that are in this repository

All you need to do is checkout this repository and use the path of the folder you want to run. Please see the example below 

1. Checkout the code from this repository (ref will tell the repository which version to use and path is where this code will be available in your repository)
      - name: Checkout code
        uses: actions/checkout@v2
      - name: Get composite run steps repository
          repository: SadaPay/composite-actions
          ref: v1
          path: ./.github/workflows
          ssh-key: ${{ secrets.DT_COMPOSITE_ACTIONS }}

2. Once you have the code checked out all you need to do is use the action of your choice
      - name: Run action from private repo
        uses: ./.github/workflows/setup-node-with-sada-registry
        with:
          token: ${{ secrets.GH_PACKAGES_READ_TOKEN }}

# How to create your own composite action

1) Create a folder at the root of the project which correctly describes the action you are trying to create. 
2) create 'action.yml' file (it has to be named action.yml or actions.yaml)
3) in the action.yml file properties name,description and runs are mandatory

Currently you cant directly access secrets in the composite actions file, you can pass them as input please see 'setup-node-with-sada-registry' as an example.
