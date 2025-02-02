---
title: 使用 Jekyll 向 GitHub Pages 站点添加主题
intro: 您可以通过添加和自定义主题来个性化 Jekyll 站点。
redirect_from:
  - /articles/customizing-css-and-html-in-your-jekyll-theme
  - /articles/adding-a-jekyll-theme-to-your-github-pages-site
  - /articles/adding-a-theme-to-your-github-pages-site-using-jekyll
  - /github/working-with-github-pages/adding-a-theme-to-your-github-pages-site-using-jekyll
  - /pages/getting-started-with-github-pages/adding-a-theme-to-your-github-pages-site-with-the-theme-chooser
product: '{% data reusables.gated-features.pages %}'
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Pages
shortTitle: Add theme to Pages site
ms.openlocfilehash: 33969695e96aa0629b2811e2742ca3093e58139a
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2022
ms.locfileid: '147644793'
---
拥有仓库写入权限的人员可以使用 Jekyll 将主题添加到 {% data variables.product.prodname_pages %} 网站。

{% data reusables.pages.test-locally %}

## 添加主题

{% data reusables.pages.navigate-site-repo %} {% data reusables.pages.navigate-publishing-source %}
2. 导航到“_config.yml”。
{% data reusables.repositories.edit-file %}
4. 为主题名称添加新行。
   - 若要使用支持的主题，请键入 `theme: THEME-NAME`，将 THEME-NAME 替换为主题存储库的 README 中显示的主题名称。 有关支持主题的列表，请参阅 {% data variables.product.prodname_pages %} 站点上的“[支持主题](https://pages.github.com/themes/)”。
   ![配置文件中支持的主题](/assets/images/help/pages/add-theme-to-config-file.png)
   - 若要使用在 {% data variables.product.prodname_dotcom %} 上托管的任何其他 Jekyll 主题，请键入 `remote_theme: THEME-NAME`，将 THEME-NAME 替换为主题存储库的 README 中显示的主题名称。
   ![配置文件中不支持的主题](/assets/images/help/pages/add-remote-theme-to-config-file.png) {% data reusables.files.write_commit_message %} {% data reusables.files.choose-commit-email %} {% data reusables.files.choose_commit_branch %} {% data reusables.files.propose_file_change %}

## 自定义主题的 CSS

{% data reusables.pages.best-with-supported-themes %}

{% data reusables.pages.theme-customization-help %}

{% data reusables.pages.navigate-site-repo %} {% data reusables.pages.navigate-publishing-source %}
1. 新建一个名为 /assets/css/style.scss 的文件。
2. 在文件顶部添加以下内容：
  ```scss
  ---
  ---

  @import "{% raw %}{{ site.theme }}{% endraw %}";
  ```
3. 在 `@import` 行的后面直接添加所需的任何自定义 CSS 或 Sass（包括导入）。

## 自定义主题的 HTML 布局

{% data reusables.pages.best-with-supported-themes %}

{% data reusables.pages.theme-customization-help %}

1. 在 {% data variables.product.prodname_dotcom %} 上，导航到主题的源仓库。 例如，Minima 的源存储库为 https://github.com/jekyll/minima 。
2. 在 _layouts 文件夹中，导航到主题的 default.html 文件。
3. 复制该文件的内容。
{% data reusables.pages.navigate-site-repo %} {% data reusables.pages.navigate-publishing-source %}
6. 创建一个名为 _layouts/default.html 的文件。
7. 粘贴之前复制的默认布局内容。
8. 根据需要自定义布局。

## 延伸阅读

- [创建新文件](/articles/creating-new-files)
