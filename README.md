name: Deploy to Preview Channel

on:
  pull_request:
    # Optionally configure to run only for specific files. For example:
    # paths:
    # - "website/**"

jobs:
  build_and_preview:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      # Add any build steps here. For example:
      # - run: npm ci && npm run build
      - uses: FirebaseExtended/action-hosting-deploy@v0
        with:
          repoToken: "${{ secrets.GITHUB_TOKEN }}"
          firebaseServiceAccount: "${{ secrets.FIREBASE_SERVICE_ACCOUNT }}"
          expires: 30d
          projectId: your-Firebase-project-ID

