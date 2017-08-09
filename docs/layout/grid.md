---
layout: docs
title: Grid 系统
description: Documentation and examples for using Bootstrap's responsive flexbox grid system.
group: layout
---
(翻译 by [AngeloZ](https://github.com/AngeloZuo/bootstrap))

Bootstrap 包含了一个强大的"移动端优先"的 flexbox 网格系统,可以为所有形式和尺寸新建布局。它是一个有多个层次,基于12列布局,并支持每个[media query 范围]({{ site.baseurl }}/layout/overview/#responsive-breakpoints)的系统。你可以通过 Sass minxin或者我们预置的 class 来使用它。

## 目录

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}

## Grid是如何工作的

Bootstrap 的 Grid 系统使用了一系列的容器(container), 行(row), 列(column)来设计和对齐内容。使用 flexbox 实现,并且完全是响应式的。下边是一个例子,可以深入的看一下 Grid 是如何结合在一起的。

<div class="bd-example bd-example-row">
<div class="container">
  <div class="row">
    <div class="col-sm">
      1/3列
    </div>
    <div class="col-sm">
      1/3列
    </div>
    <div class="col-sm">
      1/3列
    </div>
  </div>
</div>
</div>

上面的例子创建了一个三等宽列的布局,它使用了我们预置的Grid类,可以使用在小号,中号,大号和最大号尺寸的设备上。这些列之所以在页面里居中,是因为它们的父节点上有".container"类。

分步骤来看看Grid是如何起作用的:

- 容器(container)提供了一种方式可以使你的网页内容居中。在固定宽度的容器上使用".container"类或者在宽度为100%的容器上使用".container-fluid"类。

- 行(row)都是由一个个由列组成的组水平构成的,这样可以确保你所有的列可以正确的排列。我们在".row"类上使用负的外边距来确保你的所有内容相对有左侧都能正确的对齐。

- 内容需要被放置在列中, 而且, 行的直接子节点只有是列。

- 拜 flexbox 所赐, 即使没有一个确定的宽度, Grid的列也会使用相等的宽度自动的排列。比如, 四个有".col-sm"类的元素,会为小的分割点自动的变成25%的宽度。

- 在列上的类指明，在每行12列时，你想要使用的列的数目。所以，如果，你想要三等分列，你可以使用`.col-sm-4`。

- 列的宽度被设置为百分数，所以对于他们的父元素，他们一直都是流动的且尺寸是相对的。

- 所有的列都有一个水平的`padding`，能够在单独的列之间创建槽间隔（gutter），而且你可以在`.row`上使用`.no-gutters`类删除行间的`margin`和列间的`padding`。

- 一共有五种网格层，每种对应一个[响应式断点（responsive breakpoint）]({{ site.baseurl }}/layout/overview/#responsive-breakpoints)：所有断点（extra small），小号（small），中号（medium），大号（large），超大号（extra large）。

- 网格层是基于最小的宽度，意味着它们可以应用一种及其以上所有的网格层。（比如，`.col-sm-4`适用于small，medium，large，and extra large尺寸的设备）。
- You can use predefined grid classes or Sass mixins for more semantic markup.
- 你可以为语义化的标记使用预定义的网格类或者SASS的 mixin。

了解[关于flexbox的缺陷（bugs around flexbox）](https://github.com/philipwalton/flexbugs)和局限性, 比如 [不能作为flex容器的一些HTML元素（inability to use some HTML elements as flex containers）](https://github.com/philipwalton/flexbugs#9-some-html-elements-cant-be-flex-containers).

听起来还不错嘛？很好，我们一起在例子中学习这些东西吧。

## Grid options

While Bootstrap uses `em`s or `rem`s for defining most sizes, `px`s are used for grid breakpoints and container widths. This is because the viewport width is in pixels and does not change with the [font size](https://drafts.csswg.org/mediaqueries-3/#units).

See how aspects of the Bootstrap grid system work across multiple devices with a handy table.

<table class="table table-bordered table-striped table-responsive">
  <thead>
    <tr>
      <th></th>
      <th class="text-center">
        Extra small<br>
        <small>&lt;576px</small>
      </th>
      <th class="text-center">
        Small<br>
        <small>&ge;576px</small>
      </th>
      <th class="text-center">
        Medium<br>
        <small>&ge;768px</small>
      </th>
      <th class="text-center">
        Large<br>
        <small>&ge;992px</small>
      </th>
      <th class="text-center">
        Extra large<br>
        <small>&ge;1200px</small>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th class="text-nowrap" scope="row">Grid behavior</th>
      <td>Horizontal at all times</td>
      <td colspan="4">Collapsed to start, horizontal above breakpoints</td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">Max container width</th>
      <td>None (auto)</td>
      <td>540px</td>
      <td>720px</td>
      <td>960px</td>
      <td>1140px</td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">Class prefix</th>
      <td><code>.col-</code></td>
      <td><code>.col-sm-</code></td>
      <td><code>.col-md-</code></td>
      <td><code>.col-lg-</code></td>
      <td><code>.col-xl-</code></td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row"># of columns</th>
      <td colspan="5">12</td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">Gutter width</th>
      <td colspan="5">30px (15px on each side of a column)</td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">Nestable</th>
      <td colspan="5">Yes</td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">Offsets</th>
      <td colspan="5">Yes</td>
    </tr>
    <tr>
      <th class="text-nowrap" scope="row">Column ordering</th>
      <td colspan="5">Yes</td>
    </tr>
  </tbody>
</table>

## Auto-layout columns

Utilize breakpoint-specific column classes for equal-width columns. Add any number of unit-less classes for each breakpoint you need and every column will be the same width.

### Equal-width

For example, here are two grid layouts that apply to every device and viewport, from `xs` to `xl`.

<div class="bd-example-row">
{% example html %}
<div class="container">
  <div class="row">
    <div class="col">
      1 of 2
    </div>
    <div class="col">
      1 of 2
    </div>
  </div>
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col">
      1 of 3
    </div>
    <div class="col">
      1 of 3
    </div>
  </div>
</div>
{% endexample %}
</div>

### Setting one column width

Auto-layout for flexbox grid columns also means you can set the width of one column and the others will automatically resize around it. You may use predefined grid classes (as shown below), grid mixins, or inline widths. Note that the other columns will resize no matter the width of the center column.

<div class="bd-example-row">
{% example html %}
<div class="container">
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col-6">
      2 of 3 (wider)
    </div>
    <div class="col">
      3 of 3
    </div>
  </div>
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col-5">
      2 of 3 (wider)
    </div>
    <div class="col">
      3 of 3
    </div>
  </div>
</div>
{% endexample %}
</div>

### Variable width content

Using the `col-{breakpoint}-auto` classes, columns can size itself based on the natural width of its content. This is super handy with single line content like inputs, numbers, etc. This, in conjunction with [horizontal alignment](#horizontal-alignment) classes, is very useful for centering layouts with uneven column sizes as viewport width changes.

<div class="bd-example-row">
{% example html %}
<div class="container">
  <div class="row justify-content-md-center">
    <div class="col col-lg-2">
      1 of 3
    </div>
    <div class="col-12 col-md-auto">
      Variable width content
    </div>
    <div class="col col-lg-2">
      3 of 3
    </div>
  </div>
  <div class="row">
    <div class="col">
      1 of 3
    </div>
    <div class="col-12 col-md-auto">
      Variable width content
    </div>
    <div class="col col-lg-2">
      3 of 3
    </div>
  </div>
</div>
{% endexample %}
</div>

### Equal-width multi-row

Create equal-width columns that span multiple rows by inserting a `.w-100` where you want the columns to break to a new line. Make the breaks responsive by mixing the `.w-100` with some [responsive display utilities]({{ site.baseurl }}/utilities/display-property/).

<div class="bd-example-row">
{% example html %}
<div class="row">
  <div class="col">col</div>
  <div class="col">col</div>
  <div class="w-100"></div>
  <div class="col">col</div>
  <div class="col">col</div>
</div>
{% endexample %}
</div>

## Responsive classes

Bootstrap's grid includes five tiers of predefined classes for building complex responsive layouts. Customize the size of your columns on extra small, small, medium, large, or extra large devices however you see fit.

### All breakpoints

For grids that are the same from the smallest of devices to the largest, use the `.col` and `.col-*` classes. Specify a numbered class when you need a particularly sized column; otherwise, feel free to stick to `.col`.

<div class="bd-example-row">
{% example html %}
<div class="row">
  <div class="col">col</div>
  <div class="col">col</div>
  <div class="col">col</div>
  <div class="col">col</div>
</div>
<div class="row">
  <div class="col-8">col-8</div>
  <div class="col-4">col-4</div>
</div>
{% endexample %}
</div>

### Stacked to horizontal

Using a single set of `.col-sm-*` classes, you can create a basic grid system that starts out stacked on extra small devices before becoming horizontal on desktop (medium) devices.

<div class="bd-example-row">
{% example html %}
<div class="row">
  <div class="col-sm-8">col-sm-8</div>
  <div class="col-sm-4">col-sm-4</div>
</div>
<div class="row">
  <div class="col-sm">col-sm</div>
  <div class="col-sm">col-sm</div>
  <div class="col-sm">col-sm</div>
</div>
{% endexample %}
</div>

### Mix and match

Don't want your columns to simply stack in some grid tiers? Use a combination of different classes for each tier as needed. See the example below for a better idea of how it all works.

<div class="bd-example-row">
{% example html %}
<!-- Stack the columns on mobile by making one full-width and the other half-width -->
<div class="row">
  <div class="col-12 col-md-8">.col-12 .col-md-8</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
</div>

<!-- Columns start at 50% wide on mobile and bump up to 33.3% wide on desktop -->
<div class="row">
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
</div>

<!-- Columns are always 50% wide, on mobile and desktop -->
<div class="row">
  <div class="col-6">.col-6</div>
  <div class="col-6">.col-6</div>
</div>
{% endexample %}
</div>

## Alignment

Use flexbox alignment utilities to vertically and horizontally align columns.

### Vertical alignment

<div class="bd-example-row bd-example-row-flex-cols">
{% example html %}
<div class="container">
  <div class="row align-items-start">
    <div class="col">
      One of three columns
    </div>
    <div class="col">
      One of three columns
    </div>
    <div class="col">
      One of three columns
    </div>
  </div>
  <div class="row align-items-center">
    <div class="col">
      One of three columns
    </div>
    <div class="col">
      One of three columns
    </div>
    <div class="col">
      One of three columns
    </div>
  </div>
  <div class="row align-items-end">
    <div class="col">
      One of three columns
    </div>
    <div class="col">
      One of three columns
    </div>
    <div class="col">
      One of three columns
    </div>
  </div>
</div>
{% endexample %}
</div>

<div class="bd-example-row bd-example-row-flex-cols">
{% example html %}
<div class="container">
  <div class="row">
    <div class="col align-self-start">
      One of three columns
    </div>
    <div class="col align-self-center">
      One of three columns
    </div>
    <div class="col align-self-end">
      One of three columns
    </div>
  </div>
</div>
{% endexample %}
</div>

### Horizontal alignment

<div class="bd-example-row">
{% example html %}
<div class="container">
  <div class="row justify-content-start">
    <div class="col-4">
      One of two columns
    </div>
    <div class="col-4">
      One of two columns
    </div>
  </div>
  <div class="row justify-content-center">
    <div class="col-4">
      One of two columns
    </div>
    <div class="col-4">
      One of two columns
    </div>
  </div>
  <div class="row justify-content-end">
    <div class="col-4">
      One of two columns
    </div>
    <div class="col-4">
      One of two columns
    </div>
  </div>
  <div class="row justify-content-around">
    <div class="col-4">
      One of two columns
    </div>
    <div class="col-4">
      One of two columns
    </div>
  </div>
  <div class="row justify-content-between">
    <div class="col-4">
      One of two columns
    </div>
    <div class="col-4">
      One of two columns
    </div>
  </div>
</div>
{% endexample %}
</div>

### No gutters

The gutters between columns in our predefined grid classes can be removed with `.no-gutters`. This removes the negative `margin`s from `.row` and the horizontal `padding` from all immediate children columns.

Here's the source code for creating these styles. Note that column overrides are scoped to only the first children columns and are targeted via [attribute selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors). While this generates a more specific selector, column padding can still be further customized with [spacing utilities]({{ site.baseurl }}/utilities/spacing/).

{% highlight sass %}
.no-gutters {
  margin-right: 0;
  margin-left: 0;

  > .col,
  > [class*="col-"] {
    padding-right: 0;
    padding-left: 0;
  }
}
{% endhighlight %}

In practice, here's how it looks. Note you can continue to use this with all other predefined grid classes (including column widths, responsive tiers, reorders, and more).

<div class="bd-example-row">
{% example html %}
<div class="row no-gutters">
  <div class="col-12 col-sm-6 col-md-8">.col-12 .col-sm-6 .col-md-8</div>
  <div class="col-6 col-md-4">.col-6 .col-md-4</div>
</div>
{% endexample %}
</div>

### Column wrapping

If more than 12 columns are placed within a single row, each group of extra columns will, as one unit, wrap onto a new line.

<div class="bd-example-row">
{% example html %}
<div class="row">
  <div class="col-9">.col-9</div>
  <div class="col-4">.col-4<br>Since 9 + 4 = 13 &gt; 12, this 4-column-wide div gets wrapped onto a new line as one contiguous unit.</div>
  <div class="col-6">.col-6<br>Subsequent columns continue along the new line.</div>
</div>
{% endexample %}
</div>

### Column resets

With the handful of grid tiers available, you're bound to run into issues where, at certain breakpoints, your columns don't clear quite right as one is taller than the other. To fix that, use a combination of a `.clearfix` and our [responsive utility classes]({{ site.baseurl }}/layout/responsive-utilities/).

<div class="bd-example-row">
{% example html %}
<div class="row">
  <div class="col-6 col-sm-3">.col-6 .col-sm-3</div>
  <div class="col-6 col-sm-3">.col-6 .col-sm-3</div>

  <!-- Add the extra clearfix for only the required viewport -->
  <div class="clearfix hidden-sm-up"></div>

  <div class="col-6 col-sm-3">.col-6 .col-sm-3</div>
  <div class="col-6 col-sm-3">.col-6 .col-sm-3</div>
</div>
{% endexample %}
</div>

In addition to column clearing at responsive breakpoints, you may need to **reset offsets, pushes, or pulls**. See this in action in [the grid example]({{ site.baseurl }}/examples/grid/).

<div class="bd-example-row">
{% example html %}
<div class="row">
  <div class="col-sm-5 col-md-6">.col-sm-5 .col-md-6</div>
  <div class="col-sm-5 offset-sm-2 col-md-6 offset-md-0">.col-sm-5 .offset-sm-2 .col-md-6 .offset-md-0</div>
</div>

<div class="row">
  <div class="col-sm-6 col-md-5 col-lg-6">.col.col-sm-6.col-md-5.col-lg-6</div>
  <div class="col-sm-6 col-md-5 offset-md-2 col-lg-6 offset-lg-0">.col-sm-6 .col-md-5 .offset-md-2 .col-lg-6 .offset-lg-0</div>
</div>
{% endexample %}
</div>

## Reordering

### Flex order

Use flexbox utilities for controlling the **visual order** of your content.

<div class="bd-example-row">
{% example html %}
<div class="container">
  <div class="row">
    <div class="col order-0">
      First, but unordered
    </div>
    <div class="col order-last">
      Second, but last
    </div>
    <div class="col order-first">
      Third, but first
    </div>
  </div>
</div>
{% endexample %}
</div>

### Offsetting columns

Move columns to the right using `.offset-md-*` classes. These classes increase the left margin of a column by `*` columns. For example, `.offset-md-4` moves `.col-md-4` over four columns.

<div class="bd-example-row">
{% example html %}
<div class="row">
  <div class="col-md-4">.col-md-4</div>
  <div class="col-md-4 offset-md-4">.col-md-4 .offset-md-4</div>
</div>
<div class="row">
  <div class="col-md-3 offset-md-3">.col-md-3 .offset-md-3</div>
  <div class="col-md-3 offset-md-3">.col-md-3 .offset-md-3</div>
</div>
<div class="row">
  <div class="col-md-6 offset-md-3">.col-md-6 .offset-md-3</div>
</div>
{% endexample %}
</div>

### Push and pull

Easily change the order of our built-in grid columns with `.push-md-*` and `.pull-md-*` modifier classes.

<div class="bd-example-row">
{% example html %}
<div class="row">
  <div class="col-md-9 push-md-3">.col-md-9 .push-md-3</div>
  <div class="col-md-3 pull-md-9">.col-md-3 .pull-md-9</div>
</div>
{% endexample %}
</div>

## Nesting

To nest your content with the default grid, add a new `.row` and set of `.col-sm-*` columns within an existing `.col-sm-*` column. Nested rows should include a set of columns that add up to 12 or fewer (it is not required that you use all 12 available columns).

<div class="bd-example-row">
{% example html %}
<div class="row">
  <div class="col-sm-9">
    Level 1: .col-sm-9
    <div class="row">
      <div class="col-8 col-sm-6">
        Level 2: .col-8 .col-sm-6
      </div>
      <div class="col-4 col-sm-6">
        Level 2: .col-4 .col-sm-6
      </div>
    </div>
  </div>
</div>
{% endexample %}
</div>

## Sass mixins

When using Bootstrap's source Sass files, you have the option of using Sass variables and mixins to create custom, semantic, and responsive page layouts. Our [predefined grid classes](#predefined-classes) use these same variables and mixins to provide a whole suite of ready-to-use classes for fast responsive layouts.

### Variables

Variables and maps determine the number of columns, the gutter width, and the media query point at which to begin floating columns. We use these to generate the predefined grid classes documented above, as well as for the custom mixins listed below.

{% highlight scss %}
$grid-columns:      12;
$grid-gutter-width-base: 30px;

$grid-gutter-widths: (
  xs: $grid-gutter-width-base, // 30px
  sm: $grid-gutter-width-base, // 30px
  md: $grid-gutter-width-base, // 30px
  lg: $grid-gutter-width-base, // 30px
  xl: $grid-gutter-width-base  // 30px
)

$grid-breakpoints: (
  // Extra small screen / phone
  xs: 0,
  // Small screen / phone
  sm: 576px,
  // Medium screen / tablet
  md: 768px,
  // Large screen / desktop
  lg: 992px,
  // Extra large screen / wide desktop
  xl: 1200px
);

$container-max-widths: (
  sm: 540px,
  md: 720px,
  lg: 960px,
  xl: 1140px
);
{% endhighlight %}

### Mixins

Mixins are used in conjunction with the grid variables to generate semantic CSS for individual grid columns.

{% highlight scss %}
// Creates a wrapper for a series of columns
@mixin make-row($gutters: $grid-gutter-widths) {
  display: flex;
  flex-wrap: wrap;

  @each $breakpoint in map-keys($gutters) {
    @include media-breakpoint-up($breakpoint) {
      $gutter: map-get($gutters, $breakpoint);
      margin-right: ($gutter / -2);
      margin-left:  ($gutter / -2);
    }
  }
}

// Make the element grid-ready (applying everything but the width)
@mixin make-col-ready($gutters: $grid-gutter-widths) {
  position: relative;
  // Prevent columns from becoming too narrow when at smaller grid tiers by
  // always setting `width: 100%;`. This works because we use `flex` values
  // later on to override this initial width.
  width: 100%;
  min-height: 1px; // Prevent collapsing

  @each $breakpoint in map-keys($gutters) {
    @include media-breakpoint-up($breakpoint) {
      $gutter: map-get($gutters, $breakpoint);
      padding-right: ($gutter / 2);
      padding-left:  ($gutter / 2);
    }
  }
}

@mixin make-col($size, $columns: $grid-columns) {
  flex: 0 0 percentage($size / $columns);
  width: percentage($size / $columns);
  // Add a `max-width` to ensure content within each column does not blow out
  // the width of the column. Applies to IE10+ and Firefox. Chrome and Safari
  // do not appear to require this.
  max-width: percentage($size / $columns);
}

// Get fancy by offsetting, or changing the sort order
@mixin make-col-offset($size, $columns: $grid-columns) {
  margin-left: percentage($size / $columns);
}

@mixin make-col-push($size, $columns: $grid-columns) {
  left: if($size > 0, percentage($size / $columns), auto);
}

@mixin make-col-pull($size, $columns: $grid-columns) {
  right: if($size > 0, percentage($size / $columns), auto);
}
{% endhighlight %}

### Example usage

You can modify the variables to your own custom values, or just use the mixins with their default values. Here's an example of using the default settings to create a two-column layout with a gap between.

See it in action in <a href="https://jsbin.com/ruxona/edit?html,output">this rendered example</a>.

{% highlight scss %}
.container {
  max-width: 60em;
  @include make-container();
}
.row {
  @include make-row();
}
.content-main {
  @include make-col-ready();

  @media (max-width: 32em) {
    @include make-col(6);
  }
  @media (min-width: 32.1em) {
    @include make-col(8);
  }
}
.content-secondary {
  @include make-col-ready();

  @media (max-width: 32em) {
    @include make-col(6);
  }
  @media (min-width: 32.1em) {
    @include make-col(4);
  }
}
{% endhighlight %}

{% highlight html %}
<div class="container">
  <div class="row">
    <div class="content-main">...</div>
    <div class="content-secondary">...</div>
  </div>
</div>
{% endhighlight %}

## Customizing the grid

Using our built-in grid Sass variables and maps, it's possible to completely customize the predefined grid classes. Change the number of tiers, the media query dimensions, and the container widths—then recompile.

### Columns and gutters

The number of grid columns and their horizontal padding (aka, gutters) can be modified via Sass variables. `$grid-columns` is used to generate the widths (in percent) of each individual column while `$grid-gutter-widths` allows breakpoint-specific widths that are divided evenly across `padding-left` and `padding-right` for the column gutters.

{% highlight scss %}
$grid-columns:               12 !default;
$grid-gutter-width-base:     30px !default;
$grid-gutter-widths: (
  xs: $grid-gutter-width-base,
  sm: $grid-gutter-width-base,
  md: $grid-gutter-width-base,
  lg: $grid-gutter-width-base,
  xl: $grid-gutter-width-base
) !default;
{% endhighlight %}

### Grid tiers

Moving beyond the columns themselves, you may also customize the number of grid tiers. If you wanted just three grid tiers, you'd update the `$grid-breakpoints` and `$container-max-widths` to something like this:

{% highlight scss %}
$grid-breakpoints: (
  sm: 480px,
  md: 768px,
  lg: 1024px
);

$container-max-widths: (
  sm: 420px,
  md: 720px,
  lg: 960px
);
{% endhighlight %}

When making any changes to the Sass variables or maps, you'll need to save your changes and recompile. Doing so will out a brand new set of predefined grid classes for column widths, offsets, pushes, and pulls. Responsive visibility utilities will also be updated to use the custom breakpoints.
