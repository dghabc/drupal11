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
# nav设置
```
修改web/themes/custom/radixdgh/templates/form/form--search-block-form.html.twig
{%
  include "radix:form" with {
    is_inline: false,
    form_utility_classes: [
      'd-inline-flex ',
    ],
  }
%}

修改web/themes/custom/radixdgh/components/page-navigation/page-navigation.twig
	{% block right %}
		{% if page.navbar_right %}
			<div class="ms-auto d-inline-flex">
				{{ page.navbar_right }}
			</div>
		{% endif %}
	{% endblock %}
```
# 改变首页
启用bootstrap_layout_builder
在Text formats and editors 中源代码中开启允许 <div class> <i class>
设置 bootstrap-icons功能
 复制字体文件web/themes/custom/radixdgh/src/assets/fonts
复制scss文件 到web/themes/custom/radixdgh/src/scss下面
加入/home/dghabc/drupal11/web/themes/custom/radixdgh/src/scss/main.style.scss
```
@import "base/_bootstrap-icons";
修改这一行
$bootstrap-icons-font-dir: "../fonts" !default;

```


# 设置paragraphs字段
accordion item,有下面这2 个字段
 Field name                Required   Field type   Cardinality
 ------------------------- ---------- ------------ -------------
  field_accordion_content   ✔          text_long    1
  field_accordion_title     ✔          string       1
在page类型下建立了accordion items（机器名field_accordion_items） 引用了这个字段

我想建立 field--field-accordion-items.html.twig
使用radix:accordion组件效果

