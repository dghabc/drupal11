# 初始安装
```
mkdir drupal11 && cd drupal11
ddev config --project-type=drupal11 --docroot=web
ddev start
ddev composer create drupal/recommended-project:^11
ddev composer require drush/drush
ddev drush site:install --account-name=admin --account-pass=admin -y
ddev launch

git init
git remote add origin https://github.com/dghabc/drupal11.git
git add /home/dghabc/drupal11/.ddev/config.yaml -f
安装 devel masquerade radix

```

