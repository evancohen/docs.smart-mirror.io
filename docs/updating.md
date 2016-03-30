# Updating

Updating the mirror to get the latest updates is easy, just run:
```
git pull
```
This will sync the remote changes from whatever branch you are on (most likely `master`) to your local machine.

#### Encountering errors when trying to run the mirror after an update?

Sometimes new dependencies are added to the mirror or old ones are updated. In this case you need to update/install them:
```
npm update
npm install
```

There may also have been a breaking change in the format of `config.js`, which means you'll either have to fill it out again or make sure that it matches the format of `config.example.js`.

#### Still having problems?

Occasionally there can be strange issues with the changes in dependencies. In this case the easiest thing to do would be to clean your repository. This will remove all uncommitted changes (except for your config file) and re-install all dependencies:

```
git clean -xdf -e config.js
npm install
```