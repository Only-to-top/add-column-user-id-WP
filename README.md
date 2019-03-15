# add-column-user-id

```php
/*
 * Добавление колонки с ID в список пользователей в админке
 * Добавление колонки
 */
function true_user_id_column( $columns ) {
	$columns['user_id'] = 'ID';
	return $columns;
}
add_filter('manage_users_columns', 'true_user_id_column');
 
/*
 * Заполнение колонки
 */
function true_user_id_column_content($value, $column_name, $user_id) {
  if ( 'user_id' == $column_name )
    return $user_id;
  return $value;
}
add_action('manage_users_custom_column',  'true_user_id_column_content', 10, 3);

/*
 * Оформление колонки (необязательно)
 */
function true_user_id_column_style(){
  echo '<style>.column-user_id{width: 5%}</style>';
}
add_action('admin_head-users.php',  'true_user_id_column_style');
```
