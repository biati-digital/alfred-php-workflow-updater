# alfred-php-workflow-updater
A simple updater for Alfred Workflows

## How to use

```php
require_once 'updater.php';

$config = [
  'plist_url' => 'https://externalsite.com/info.plist',
  'workflow_url' => 'https://externalsite.com/Calculate.Anything.alfredworkflow',
  'check_interval => 86400 * 15,
  'force_check' => false,
  'force_download' => false,
  'download_type' => 'async',
];
$updater = new Alfred\Updater($config);

return $updater->checkUpdates();
```

## Options

#### check_interval
The interval in seconds between update checks, default 15 days.

#### plist_url
the url to the remote plist file, used to check for new versions, the updater will download this file and compare the local workflow version with the version of this file. If you host your workflow on Github you can use a URL like this:

https://raw.githubusercontent.com/{githubuser}/{project}/master/info.plist

#### workflow_url
URL to the .workflow file, if an update is available, the workflow will be downloaded and opened so it can be installed. If you host your workflow on Github you can use a URL like this:

https://github.com/{githubuser}/{project}/releases/latest/download/Calculate.Anything.alfredworkflow


#### force_check
Bypass the cache and check again the remote plist.

#### force_download
Force the download of the latest version even if there are no updates available, useful for tests.

#### download_type
Type of download, available methods are async or sync.
