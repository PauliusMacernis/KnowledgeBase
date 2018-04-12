## PHP (Composer)
- What's the difference between `composer update` and `composer install`?
<a href="#" title="compoaser update is dangerous because it will bring in new versions of packages which you haven't tested to work fine in your app. composer install will not update anything; it will just install all the dependencies as specified in the composer.lock file. composer update is mostly used in the 'development phase', to upgrade our project packages according to what we have specified in the composer.json file. composer install is primarily used in the 'deploying phase' to install our application on a production server or on a testing environment, using the same dependencies stored in the composer.lock file created by composer update.
http://stackoverflow.com/questions/33052195/what-are-the-differences-between-composer-update-and-composer-install
 ">⌘</a>
 
 - **Explain `composer create-project --prefer-dist laravel/lumen docker-lamp`**  
 This is the equivalent of doing a `git clone/svn checkout` followed by a `composer install` of the vendors.  
 ```
 Options

    --stability (-s):       Minimum stability of package. Defaults to stable.
    --prefer-source:        Install packages from source when available.
    --prefer-dist:          Install packages from dist when available.
    --repository:           Provide a custom repository to search for the package, which will be used instead of packagist. Can be either an HTTP URL pointing to a composer repository, a path to a local packages.json file, or a JSON string which similar to what the repositories key accepts.
    --dev:                  Install packages listed in require-dev.
    --no-dev:               Disables installation of require-dev packages.
    --no-scripts:           Disables the execution of the scripts defined in the root package.
    --no-progress:          Removes the progress display that can mess with some terminals or scripts which don't handle backspace characters.
    --no-secure-http:       Disable the secure-http config option temporarily while installing the root package. Use at your own risk. Using this flag is a bad idea.
    --keep-vcs:             Skip the deletion of the VCS metadata for the created project. This is mostly useful if you run the command in non-interactive mode.
    --remove-vcs:           Force-remove the VCS metadata without prompting.
    --no-install:           Disables installation of the vendors.
    --ignore-platform-reqs: ignore php, hhvm, lib-* and ext-* requirements and force the installation even if the local machine does not fulfill these.

 ```
 
 
