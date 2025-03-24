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

# 安装radixdgh子模板

```
ddev drush --include="web/themes/contrib/radix" radix:create radixdgh
ddev drush then radixdgh -y; ddev drush config-set system.theme default radixdgh -y
cd web/themes/custom/radixdgh
nvm use
npm install
cp .env.example .env.local
//修改DRUPAL_BASE_URL=https://drupal11.ddev.site/
ddev theme:watch radixdgh
```
修改navbar为黑色
https://bootswatch.com/sandstone/
这个配色

#
