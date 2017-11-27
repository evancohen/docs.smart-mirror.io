# Updating

Updating the mirror to get the latest updates is easy, just run:

```
git pull && npm install
```

This will sync the remote changes from whatever branch you are on \(most likely `master`\) to your local machine. This will also install/update any new or updated dependencies.

#### Encountering errors when trying to run the mirror after an update?

Sometimes new dependencies are added to the mirror or old ones are updated. In this case you need to update/install them:

```
npm update
npm install
```

#### Still having problems?

Occasionally there can be strange issues with the changes in dependencies. In this case the easiest thing to do would be to clean your repository. This will remove all uncommitted changes \(except for your config file\) and re-install all dependencies:

```
git clean -xdf -e config.json
npm install
```



