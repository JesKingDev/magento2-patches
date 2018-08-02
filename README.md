# magento2-patches
Patches that relate to specific PR's to be used with https://github.com/vaimo/composer-patches

## Usage

The patches have been created to be used for composer M2 projects.

So if you have used steps described at http://devdocs.magento.com/guides/v2.0/install-gde/prereq/integrator_install.html, 
you should have a M2 project that has composer.json at it's core that dicrates which packages are installed.

1. In project root folder: composer require vaimo/composer-patches
2. Copy the patches you want to use under <project-root>/patches
3. The project composer.json should also already have an "extra" key defined. if you add new sub-key there called 
   "patches" (see above), then the next time you do "composer update", the modules that have patches defined will 
   be re-installed and patches applied. Patches have file-target paths that are relative to composer packages which 
   means that the context defined in composer.json is pretty important and patches are not directly appliable in context 
   on magento/magento2 repository, but they're ripe to be used for composer project.
   
```json
{

    "require": {
        "vaimo/composer-patches": "~1.4.0",
    },

    "extra": {
        "patches": {
            "magento/module-catalog": {
                "Fix: https://github.com/magento/magento2/issues/5438": "patches/Patch-Magento_Catalog-M2.1.0-image-attribute-backend-model-hardcoded-attribute-code-removal.patch"
            },
            "magento/module-ui": {
                "Fix: https://github.com/magento/magento2/issues/5438": "patches/Patch-Magento_Ui-M2.1.0-allow-backend-to-know-the-origin-input-of-the-upload-request.patch"
            },
        }
    }

}
```
