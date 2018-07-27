# Structure Manager
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/e4d11f692afc45769893a5299069e643)](https://www.codacy.com/app/laravel-enso/StructureManager?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=laravel-enso/StructureManager&amp;utm_campaign=Badge_Grade)
[![StyleCI](https://styleci.io/repos/95235866/shield?branch=master)](https://styleci.io/repos/95235866)
[![License](https://poser.pugx.org/laravel-enso/structuremanager/license)](https://packagist.org/packages/laravel-enso/structuremanager)
[![Total Downloads](https://poser.pugx.org/laravel-enso/structuremanager/downloads)](https://packagist.org/packages/laravel-enso/structuremanager)
[![Latest Stable Version](https://poser.pugx.org/laravel-enso/structuremanager/version)](https://packagist.org/packages/laravel-enso/structuremanager)

Resource generation CLI & Structure Manager dependency for [Laravel Enso](https://github.com/laravel-enso/Enso)

[![Watch the demo](https://laravel-enso.github.io/structuremanager/screenshots/bulma_001_thumb.png)](https://laravel-enso.github.io/structuremanager/videos/bulma_demo01.mp4)
<sup>click on the photo to view a short demo in compatible browsers</sup>

## Features
- comes with its own easy to use CLI for the creation of Enso resources
- can be used to more easily insert (default) data, during the install of a package, or later when new routes and permissions are required and can create menus, assign default permissions, etc.
- extends Illuminate's `Migration` class and acts like a migration
- can also rollback its own changes
- when adding menus and permissions, automatic access for the administrator role is added

    
## CLI Details
The command line interface is a powerful tool meant to help you quickly create the needed files structure
when adding new resources for your application.

You can use it to create:
* menus
* permissions and permission groups
* models
* front-end routes
* back-end routes
* [FormBuilder](https://github.com/laravel-enso/FormBuilder)
    * form builders
    * json templates (boilerplate)
    * specific validation request
    * form controllers
* [VueDatatable](https://github.com/laravel-enso/VueDatatable) 
    * table builders
    * table templates (boilerplate)
    * table controllers
* [Select](https://github.com/laravel-enso/Select)
    * controllers

### CLI Usage
You may run the CLI with the following command:
```bash
php artisan enso:make:structure
```

You'll be presented with a menu you may use for configuring the creation of resources.
Some of the options may depend on other options, so if you choose something that has such
dependencies, you'll be notified.

The CLI menu options are listed in a logical order, as, for instance, 
you can't add Permissions without first specifying a Permission Group. 

When choosing an option, you'll also be presented with the current configuration for that option
especially useful when going back to edit some of the options.

When editing an option, you may start typing to get an autocomplete option, 
for the currently configured value.

After configuring the desired options, you should select the **Files** you want generated.

When satisfied with your selection, use the **Generate** option to have the files created.

Once the files are generated, depending on your choices, 
you'll also be presented with the backend routes you'll need to paste in your `routes/api.php` file.

If you've created front-end resources, don't forget to rebuild your js resources, 
using `npm run webpack` or similar.

The available options are listed below:

#### [0] Model
- type in a name for the model;

As per the Laravel convention, models should be upper-camel-cased

#### [1] Permission Group
- type in the name for the permission group

Note that per Enso convention, the name must coincide with the common part of the resource permission. 
For example, `administration.users` is used for the Users' permission group. 

#### [2] Permissions
- select which resources you want permissions generated for

The permissions will be generated for you, there is no need to configure anything else here.

#### [3] Menu
- type a name for the menu; this will be the user-visible label
- type in the desired Font Awesome icon class; make sure to have the given class imported and available  
- type in the name of the parent menu, if applicable (for example `Administration`)
- type in the name of the route used when clicking on the menu (for example `administration.users.index`)
- type in the order index for this menu element; This is used for the ordering of the menus and submenus 
- choose whether a certain menu will have children

#### [4] Files
- choose which files you want generated by the tool

Note than one selection will generate the required files for that resource, 
for instance, choosing `model` will generate just the model class, but choosing `form`
 will generate a controller, a builder, a template and a validation request.

#### [5] Generate
Choosing this option will generate the files based on your configuration and selections.

## Commands
- `php artisan enso::make:structure` - runs the structure creation CLI 

## Notes

The [Laravel Enso Core](https://github.com/laravel-enso/Core) package comes with this package included.

Depends on:
- depends on [PermissionManager](https://github.com/laravel-enso/PermissionManager) as it uses it for permissions handling
- depends on [MenuManager](https://github.com/laravel-enso/MenuManager) for the creation of menus, when required
- depends on [RoleManager](https://github.com/laravel-enso/RoleManager) for the integration with roles, when adding default permissions