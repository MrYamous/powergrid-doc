# Table Header & Footer

This section covers the features of your Table Component Header and Footer.

Here you will find:

[[toc]]

## Header

In this subsection, you will find how to configure your Table Header.

### Multi-row Bulk Actions

See [Bulk Actions](/table-features/bulk-actions.html).

---

### Search Input

Display a global data search input in your Table header.

To enable this feature, proceed to chain the `showSearchInput()` method to the `PowerGrid::header()` class call.

You may read how to configure this feature in the [Searching Data](/table-features/searching-data.html) section.

Example:

```php
// app/Livewire/DishTable.php

use PowerComponents\LivewirePowerGrid\PowerGridComponent;
use PowerComponents\LivewirePowerGrid\Facades\PowerGrid; // [!code ++]

class DishTable extends PowerGridComponent
{
    public function setUp(): array
    {
        return [
            PowerGrid::header()// [!code ++]
                ->showSearchInput(),// [!code ++]
        ];
    }
}
```

::: info 📝 NOTE
Currently, this function does not support Enum fields.
:::

---

### Toggle Column Visibility

Display a button to hide and show columns (toggle visibility) in your Table header.

To enable this feature, proceed to chain the `showToggleColumns()` method to the `PowerGrid::header()` class call.

Example:

```php
// app/Livewire/DishTable.php

use PowerComponents\LivewirePowerGrid\PowerGridComponent;
use PowerComponents\LivewirePowerGrid\Facades\PowerGrid; // [!code ++]

class DishTable extends PowerGridComponent
{
    public function setUp(): array
    {
        return [
             PowerGrid::header() // [!code ++]
                ->showToggleColumns(),// [!code ++]
        ];
    }
}
```

---

### Loading Icon

By default, PowerGrid displays a loading icon every time a server request is made.

To disable this feature, proceed to chain the `withoutLoading()` method to the `PowerGrid::header()` class call.

```php
// app/Livewire/DishTable.php

use PowerComponents\LivewirePowerGrid\PowerGridComponent;
use PowerComponents\LivewirePowerGrid\Facades\PowerGrid; // [!code ++]

class DishTable extends PowerGridComponent
{
    public function setUp(): array
    {
        return [
            PowerGrid::header()// [!code ++]
                ->withoutLoading(),// [!code ++]
        ];
    }
}
```

---

### Display Soft Deleted Records

Adds a button to the Table header to control which records are being displayed: "With deleted records", "Without deleted records" or "Only deleted records".

To enable this feature, proceed to chain the `showSoftDeletes()` method to the `PowerGrid::header()` class call.

Example:

```php
// app/Livewire/DishTable.php

use PowerComponents\LivewirePowerGrid\PowerGridComponent;
use PowerComponents\LivewirePowerGrid\Facades\PowerGrid; // [!code ++]

class DishTable extends PowerGridComponent
{
    public function setUp(): array
    {
        return [
            PowerGrid::header()// [!code ++]
                ->showSoftDeletes(showMessage: true),// [!code ++]
        ];
    }
}
```

By default, a message will be displayed to inform what records are being displayed. You can disable this message passing the parameter `$showMessage = false`.

<div class="onlinedemo custom-block">
  <p class="custom-block-title">🚀 See it in action</p>
  <p>See an interactive example using <a target="_blank" href="https://demo.livewire-powergrid.com/examples/show-soft-delete">Soft Deletes</a>.</p>

</div>

## Footer

In this subsection, you will find how to configure your Table Footer.

### Pagination

See the dedicated section for [Pagination](/table-features/pagination.html).

## Personalizing Header & Footer

### Include View on Top

Sometimes, we need to reuse the current scope of the Table using `@include` instead of using events.

To add a view, proceed to chain the `includeViewOnTop()` method to either the `PowerGrid::header()` or `PowerGrid::footer()` class call.

```php
// app/Livewire/DishTable.php

use PowerComponents\LivewirePowerGrid\PowerGridComponent;
use PowerComponents\LivewirePowerGrid\Facades\PowerGrid; // [!code ++]

class DishTable extends PowerGridComponent
{
    public string $someProperty =  "foobar"; // [!code highlight:1]

    public function setUp(): array
    {
        return [
            PowerGrid::footer()// [!code ++]
                ->includeViewOnTop('components.datatable.footer-top'), // [!code ++]
        ];
    }
}
```

You may use your Component's property in your custom view as the demonstrated below:

```php
{{-- resources/views/components/datatable/footer-top.blade.php --}}

<div>
    This is my property: {{ $someProperty }}
</div>
```

<div class="onlinedemo custom-block">
  <p class="custom-block-title">🚀 See it in action</p>
  <p>See an interactive example using <a target="_blank" href="https://demo.livewire-powergrid.com/examples/custom-theme">Include View on Top</a>.</p>

</div>

---

### Include View on Bottom

Sometimes, we need to reuse the current scope of the Table using `@include` instead of using events.

To add a view, proceed to chain the `includeViewOnBottom()` method to either the `PowerGrid::header()` or `PowerGrid::footer()` class call.

```php
// app/Livewire/DishTable.php

use PowerComponents\LivewirePowerGrid\PowerGridComponent;
use PowerComponents\LivewirePowerGrid\Facades\PowerGrid; // [!code ++]

class DishTable extends PowerGridComponent
{
    public string $someProperty =  "foobar"; // [!code highlight:1]

    public function setUp(): array
    {
        return [
            PowerGrid::header()// [!code ++]
                ->includeViewOnBottom('components.datatable.header-bottom'), // [!code ++]
        ];
    }
}
```

You may use your Component's property in your custom view as the demonstrated below:

```php
{{-- resources/views/components/datatable/header-bottom.blade.php --}}

<div>
    This is my property: {{ $someProperty }}
</div>
```

If you need to customize the pagination, visit the section to learn more about [Custom Pagination Component](/table-features/pagination.html#custom-pagination-component).

<div class="onlinedemo custom-block">
  <p class="custom-block-title">🚀 See it in action</p>
  <p>See an interactive example using <a target="_blank" href="https://demo.livewire-powergrid.com/examples/custom-theme">Include View on Bottom</a>.</p>

</div>
