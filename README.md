# magento2-patches
Patches that relate to specific PR's to be used with https://github.com/cweagans/composer-patches

## Usage

The patches have been created to be used for composer M2 projects.

1. In project root folder, run these commands:

```bash
composer config repositories.ripen-patches vcs https://github.com/ripenecommerce/magento2-patches.git
composer require ripenecommerce/magento2-patches=dev-master
```

2. The project `composer.json` should also already have an "extra" key defined. Add a new sub-key there called 
   "patches" along with the specific patch definitions to apply (see last section below). Then the next time you do
   `composer update`, the modules that have patches defined will be re-installed and patches applied. 

## Patch Creation

TODO: Complete instructions.

Patches have file-target paths that are relative to composer packages.

## Definitions for Patches

Note: This is not intended to be copied and pasted in full, as these patches apply to different version of
Magento (see the respective GitHub issue or pull request for details on what patches are needed in what
versions). Instead, excerpt only the entry for the patch you know you need.

```json
{
    "extra": {
        "patches": {
            "magento/framework": {
                "Fix: https://github.com/magento/magento2/issues/13213 Version < 2.2.4 only.":
                "https://raw.githubusercontent.com/JesKingDev/magento2-patches/master/Patch-Magento_Framework-13213_admin_customer_edit_error.patch"
            },
            "magento/module-catalog": {
                "Fix: Store View specific pricing not being indexed properly":
                "https://raw.githubusercontent.com/JesKingDev/magento2-patches/master/Patch-Magento_Catalog-M2.2-price-indexing-by-store-view.patch",
                "Fix: https://github.com/magento/magento2/issues/5438":
                "https://raw.githubusercontent.com/ripenecommerce/magento2-patches/master/Patch-Magento_Catalog-M2.1.0-image-attribute-backend-model-hardcoded-attribute-code-removal.patch",

                "Fix: https://github.com/magento/magento2/issues/6076":
                "https://raw.githubusercontent.com/ripenecommerce/magento2-patches/master/Patch-Magento_Catalog-0001-MAGETWO-54223-CMS-Widgets-Catalog-Category-Link-widg.patch",

                "Fix: https://github.com/magento/magento2/issues/5931 and https://github.com/magento/magento2/issues/5612":
                "https://raw.githubusercontent.com/ripenecommerce/magento2-patches/master/Patch-Magento_Catalog-M2.1.5-MAGETWO-56410-MAGETWO-56411-github-issues-5931-5612.patch"
            },
            "magento/module-customer": {
                "Fix: https://github.com/magento/magento2/issues/10838. Version < M2.2.2 only.":
                "https://raw.githubusercontent.com/ripenecommerce/magento2-patches/Patch-Magento-Customer-grid-indexer-add-missing-function.patch"
            },
            "magento/module-framework": {
                "Fix: https://github.com/magento/magento2/issues/10838. Version M2.2.2+":
                "https://raw.githubusercontent.com/JesKingDev/magento2-patches/master/Patch-MAGETWO-90109-Customer_Grid_Indexer_Not_Working.patch"          
            },
            "magento/module-payment": {
                "Fix: https://github.com/magento/magento2/pull/9365":
                "https://raw.githubusercontent.com/ripenecommerce/magento2-patches/master/Patch-Magento_Payment-M2.1.3-MAGETWO-60351-optimize-payment-methods-checkout.patch"
            },
            "magento/module-ui": {
                "Fix: https://github.com/magento/magento2/issues/5438":
                "https://raw.githubusercontent.com/ripenecommerce/magento2-patches/master/Patch-Magento_Ui-M2.1.0-allow-backend-to-know-the-origin-input-of-the-upload-request.patch"
            },
            "magento/module-vault": {
                "Fix: https://github.com/magento/magento2/pull/9365":
                "https://raw.githubusercontent.com/ripenecommerce/magento2-patches/master/Patch-Magento_Vault-M2.1.3-MAGETWO-60351-optimize-payment-methods-checkout.patch"
            },
            "magento/magento2-base": {
                "Fix: https://github.com/magento/magento2/issues/4232":
                "https://raw.githubusercontent.com/ripenecommerce/magento2-patches/master/Patch-Magento_Base-0001-MAGETWO-52850-GitHub-UTF-8-special-character-issue-i.patch"
            },
            "magemojo/m2-ce-cron": {
                "Fix: https://github.com/magemojo/m2-ce-cron/issues/40 (Version < 1.2.3 only)":
                "https://raw.githubusercontent.com/JesKingDev/magento2-patches/master/MageMojo/Cron/Patch-40_duplicate_cron_execution.diff",
                "Fix: https://github.com/magemojo/m2-ce-cron/issues/44":
                "https://raw.githubusercontent.com/JesKingDev/magento2-patches/master/MageMojo/Cron/Patch-44_maintenance_exempt_ips.diff"
            },
            "mirasvit/module-blog": {
                "Fix: https://github.com/mirasvit/module-blog/issues/136": 
                "https://raw.githubusercontent.com/JesKingDev/magento2-patches/master/Mirasvit/module-blog/136__fix_class_exception.diff"
            }

        }
    }
}
```
