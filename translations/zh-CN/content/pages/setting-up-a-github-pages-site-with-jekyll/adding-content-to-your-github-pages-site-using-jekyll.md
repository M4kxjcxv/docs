---
title: 使用 Jekyll 向 GitHub Pages 站点添加内容
intro: '您可以在 {% data variables.product.prodname_pages %} 上向 Jekyll 站点添加新页面或帖子。'
product: '{% data reusables.gated-features.pages %}'
redirect_from:
  - /articles/adding-content-to-your-github-pages-site-using-jekyll
  - /github/working-with-github-pages/adding-content-to-your-github-pages-site-using-jekyll
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Pages
shortTitle: Add content to Pages site
ms.openlocfilehash: 90bd0d067837364eb2767739da286da7906399c0
ms.sourcegitcommit: 47bd0e48c7dba1dde49baff60bc1eddc91ab10c5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2022
ms.locfileid: '145130245'
---
拥有仓库写入权限的人员可以使用 Jekyll 向 {% data variables.product.prodname_pages %} 站点添加内容。

## 关于 Jekyll 站点中的内容

必须先创建一个 Jekyll 站点，然后才可将内容添加到 {% data variables.product.prodname_pages %} 上的 Jekyll 站点。 有关详细信息，请参阅“[使用 Jekyll 创建 {% data variables.product.prodname_pages %} 站点](/articles/creating-a-github-pages-site-with-jekyll)”。

Jekyll 站点中内容的主要类型是页面和帖子。 页面是指与某个特定日期没有关联的独立内容，例如“关于”页面。 默认的 Jekyll 站点包含一个名为 `about.md` 的文件，该文件在 `YOUR-SITE-URL/about` 呈现为站点上的一个页面。 您可以编辑该文件的内容以个性化“关于”页面，也可以使用“关于”页作为模板创建新页面。 有关详细信息，请参阅 Jekyll 文档中的“[页面](https://jekyllrb.com/docs/pages/)”。

帖子是博客文章。 默认 Jekyll 站点包含名为 `_posts` 的目录，其中包含默认帖子文件。 您可以编辑该帖子的内容，也可以将默认帖子用作模板来创建新帖子。 有关详细信息，请参阅 Jekyll 文档中的“[帖子](https://jekyllrb.com/docs/posts/)”。

主题包括默认布局、包含和样式表，它们将自动应用到站点上的新页面和帖子，但您可以覆盖其中任何默认值。 有关详细信息，请参阅“[关于 {% data variables.product.prodname_pages %} 和 Jekyll](/articles/about-github-pages-and-jekyll#themes)”。

{% data reusables.pages.about-front-matter %}

{% data reusables.pages.test-locally %}

## 向站点添加新页面

{% data reusables.pages.navigate-site-repo %} {% data reusables.pages.navigate-publishing-source %}
3. 在发布源的根目录中，为名为 PAGE-NAME.md 的页面创建新文件，将 PAGE-NAME 替换为对该页面有意义的文件名 。
4. 在文件顶部添加以下 YAML 前页，将 PAGE TITLE 替换为页面的标题，将 URL-PATH 替换为想要的页面 URL 的路径 。 例如，如果站点的基 URL 为 `https://octocat.github.io`，并且 URL-PATH 为 `/about/contact/`，则页面将位于 `https://octocat.github.io/about/contact`。
  ```shell
  layout: page
  title: "<em>PAGE TITLE</em>"
  permalink: /<em>URL-PATH</em>/
  ```
5. 在前页下方，为页面添加内容。
{% data reusables.files.write_commit_message %} {% data reusables.files.choose-commit-email %} {% data reusables.files.choose_commit_branch %} {% data reusables.files.propose_file_change %} {% data reusables.files.choose_pull_request %} {% data reusables.files.merge_pull_request %} {% data reusables.files.write_commit_message_pull_request %} {% data reusables.files.confirm_merge %} {% data reusables.files.delete_branch %}

## 向站点添加新帖子

{% data reusables.pages.navigate-site-repo %} {% data reusables.pages.navigate-publishing-source %}
3. 导航到 `_posts` 目录。
4. 创建名为 YYYY-MM-DD-NAME-OF-POST.md 的新文件，将 YYYY-MM-DD 替换为帖子的日期，将 NAME-OF-POST 替换为帖子的名称  。
4. 在文件顶部添加以下 YAML 前页，将 POST TITLE 替换为帖子标题，将 YYYY-MM-DD hh:mm:ss -0000 替换为帖子的日期和时间，将 CATEGORY-1 和 CATEGORY-2 替换为要为帖子选择的多个类别   。
  ```shell
  layout: post
  title: "<em>POST TITLE</em>"
  date: </em>YYYY-MM-DD hh:mm:ss -0000</em>
  categories: <em>CATEGORY-1</em> <em>CATEGORY-2</em>
  ```
5. 在前页下方，为帖子添加内容。
{% data reusables.files.write_commit_message %} {% data reusables.files.choose-commit-email %} {% data reusables.files.choose_commit_branch %} {% data reusables.files.propose_file_change %} {% data reusables.files.choose_pull_request %} {% data reusables.files.merge_pull_request %} {% data reusables.files.write_commit_message_pull_request %} {% data reusables.files.confirm_merge %} {% data reusables.files.delete_branch %}

您的帖子现在应该显示在您的站点上！ 如果站点的基 URL 为 `https://octocat.github.io`，则新帖子将位于 `https://octocat.github.io/YYYY/MM/DD/TITLE.html`。

## 后续步骤

{% data reusables.pages.add-jekyll-theme %} 有关详细信息，请参阅“[使用 Jekyll 将主题添加到 {% data variables.product.prodname_pages %} 站点](/articles/adding-a-theme-to-your-github-pages-site-using-jekyll)”。
