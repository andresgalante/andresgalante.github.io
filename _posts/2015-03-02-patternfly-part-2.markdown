---
layout: post
title:  "Advance Patternfly settings"
date:   2015-03-06 23:05:36
categories: howto
---

A few weeks ago I wrote [how to set up Patternfly to start a new project](/howto/2015/02/06/patternfly.html). This time I am going to dive deeper into Patternfly and Boostrap structures to customise and minimise the impact on the compiled css.

Patternfly imports Boostrap, and we import Patternfly as a base for our less file.

When we concatenate the base layer of Boostrap styling plus the second layer of Patternfly styles plus our styles by importing one into the other, we end up with a huge css that defines classes and structures that we might never use.

For example, if our project doesn't use the modal component, there is no point in loading it to our css.

To achieve this customisation of component we are going to look into the nuts and bolts of patternfly and Boostrap.

## Import what really matters 

Until now we created a `styles.less` files that imports patternfly like this:

{% highlight css %}
@import "../bower_components/patternfly/less/patternfly.less";
{% endhighlight %}

As I mention before this will compile into a huge css files. 

In order to import just the parts of patternfly and bootstrap that matters to our project, we are going to look into `bootrap.less` and `patternfly.less`

*TIP* By keeping `/bower_components` untouched, you'll be able to bower updates.


## Boostrap layer

Lets start from the base: Bootstrap.

When we use bower to install Patternfly, we also install Bootsrap as a component. Open `bootstrap.less` on your text editor, you'll find it under `bower_components/patternfly/components/Boostrap/less/Boostrap.less`

There is a list of core and component styles. These are the steps to do:

- Select all in `bootstrap.less `
- Copy
- Open `styles.less`
- Paste it on the beginning of `styles.less`
- Change the path of the imports so they point to the correct location `../bower_components/patternfly/components/Boostrap/less/NAME_OF_THE_FILE`

Now, don't touch the core elements, you'll need those to do the base styling like typography settings, grids, etc.

Go through the list of component and comment out with a '//' the ones you'll not use. Let's say your project doesn't use breadcrumbs or pagination, go ahead and comment those out:

{% highlight css %}
// Components
@import "../bower_components/patternfly/components/Boostrap/less/component-animations.less";
@import "../bower_components/patternfly/components/Boostrap/less/glyphicons.less";
@import "../bower_components/patternfly/components/Boostrap/less/dropdowns.less";
@import "../bower_components/patternfly/components/Boostrap/less/button-groups.less";
@import "../bower_components/patternfly/components/Boostrap/less/input-groups.less";
@import "../bower_components/patternfly/components/Boostrap/less/navs.less";
@import "../bower_components/patternfly/components/Boostrap/less/navbar.less";
// @import "../bower_components/patternfly/components/Boostrap/less/breadcrumbs.less";
// @import "../bower_components/patternfly/components/Boostrap/less/pagination.less";
@import "../bower_components/patternfly/components/Boostrap/less/pager.less";
@import "../bower_components/patternfly/components/Boostrap/less/labels.less";
@import "../bower_components/patternfly/components/Boostrap/less/badges.less";
@import "../bower_components/patternfly/components/Boostrap/less/jumbotron.less";
@import "../bower_components/patternfly/components/Boostrap/less/thumbnails.less";
@import "../bower_components/patternfly/components/Boostrap/less/alerts.less";
@import "../bower_components/patternfly/components/Boostrap/less/progress-bars.less";
@import "../bower_components/patternfly/components/Boostrap/less/media.less";
@import "../bower_components/patternfly/components/Boostrap/less/list-group.less";
@import "../bower_components/patternfly/components/Boostrap/less/panels.less";
@import "../bower_components/patternfly/components/Boostrap/less/wells.less";
@import "../bower_components/patternfly/components/Boostrap/less/close.less";
{% endhighlight %}

## Patternfly layer

Now lets do the same with patternfly styles. Open `patternfly.less` on your text editor, you'll find it under `/bower_components/patternfly/less/patternfly.less` and repeat the same steps: select, copy, paste and change the path.

*IMPORTANT* Remember to paste patternfly styles after bootstrap styles.

Lets go back to our previews example, we are not using breadcrumbs or pagination, so we comment out those lines:

{% highlight css %}
/* PatternFly overrides and new stuff */
@import "../bower_components/patternfly/less/variables.less";
@import "../bower_components/patternfly/less/mixins.less";
@import "../bower_components/patternfly/less/alerts.less";
@import "../bower_components/patternfly/less/badges.less";
@import "../bower_components/patternfly/less/bootstrap-combobox.less";
@import "../bower_components/patternfly/less/bootstrap-select.less";
@import "../bower_components/patternfly/less/bootstrap-treeview.less";
// @import "../bower_components/patternfly/less/breadcrumbs.less";
@import "../bower_components/patternfly/less/buttons.less";
@import "../bower_components/patternfly/less/close.less";
@import "../bower_components/patternfly/less/datatables.less";
@import "../bower_components/patternfly/less/dropdowns.less";
@import "../bower_components/patternfly/less/fonts.less";
@import "../bower_components/patternfly/less/forms.less";
@import "../bower_components/patternfly/less/icons.less";
@import "../bower_components/patternfly/less/infotip.less";
@import "../bower_components/patternfly/less/labels.less";
@import "../bower_components/patternfly/less/list-group.less";
@import "../bower_components/patternfly/less/login.less";
@import "../bower_components/patternfly/less/modals.less";
@import "../bower_components/patternfly/less/navbar.less";
@import "../bower_components/patternfly/less/pager.less";
// @import "../bower_components/patternfly/less/pagination.less";
@import "../bower_components/patternfly/less/panels.less";
@import "../bower_components/patternfly/less/popovers.less";
@import "../bower_components/patternfly/less/progress-bars.less";
@import "../bower_components/patternfly/less/search.less";
@import "../bower_components/patternfly/less/sidebar.less";
@import "../bower_components/patternfly/less/spinner.less";
@import "../bower_components/patternfly/less/tables.less";
@import "../bower_components/patternfly/less/tabs.less";
@import "../bower_components/patternfly/less/tooltip.less";
@import "../bower_components/patternfly/less/type.less";
{% endhighlight %}


## Your styles layer

*IMPORTANT* Remember **not** to include a call to patternfly.less `@import "/bower_components/patternfly/less/variables.less";`

Write your styles after Patternfly styles on styles.less.

Once compiled,  styles.css generated from styles.less will not include any reference to breadcrumbs or pagination, making it lighter and faster to load.

## Better comment out than delete

Any comment with less `//` will not became part of the compiled css. It's good to keep them commented in case you want to add that component later in the project.

You'll want your production code to be as clean as possible. Sending less code is cheaper and faster.