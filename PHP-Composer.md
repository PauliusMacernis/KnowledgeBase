## PHP (Composer)
- What's the difference between `composer update` and `composer install`?
<a href="#" title="compoaser update is dangerous because it will bring in new versions of packages which you haven't tested to work fine in your app. composer install will not update anything; it will just install all the dependencies as specified in the composer.lock file. composer update is mostly used in the 'development phase', to upgrade our project packages according to what we have specified in the composer.json file. composer install is primarily used in the 'deploying phase' to install our application on a production server or on a testing environment, using the same dependencies stored in the composer.lock file created by composer update.
http://stackoverflow.com/questions/33052195/what-are-the-differences-between-composer-update-and-composer-install
 ">⌘</a>
