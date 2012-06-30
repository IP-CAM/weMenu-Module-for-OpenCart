## weMenu
======

Module for OpenCart

## Использование

Так как данные меню храняться в системных настройках, меню можно вывести в любом месте на странице, тем самым не ограничиваясь «расположениями»

Просто вставьте следующий код в любой шаблон, например в `/catalog/view/theme/default/template/common/header.tpl`

```php
<?php if($we_menu_cache = $this->config->get('we_menu_cache')){ ?> 
    <ul class="<?php echo $this->config->get('we_menu_class') ?>">
        <?php if(!empty($we_menu_cache)){ ?>
            <?php foreach($we_menu_cache as $item){ 
                $tpl = strstr($item['href'], $_SERVER['REQUEST_URI']) && $_SERVER['REQUEST_URI'] != '/'  ? 'tpl_row_act' : 'tpl_row';
                echo html_entity_decode($item[$tpl]); 
                } ?>
        <?php } ?>
    </ul>
<?php } ?>
```