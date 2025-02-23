name:site
on:
  push:
    branches:
      - main  # Adjust if your default branch is different

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout the repository
      uses: actions/checkout@v2

    - name: Set up Node.js
      uses: actions/setup-node@v2
      with:
        node-version: '14'

    - name: Install dependencies
      run: npm install

    - name: Build the project
      run: npm run build  # Adjust if your build command is different

    - name: Deploy to GitHub Pages
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
        publish_dir: ./dist  # Adjust if your output directory is different
