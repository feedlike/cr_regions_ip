Сr Region IP RUS
=============

Wordpress плагин для определения города и региона Российской Федерации по ip посетителя

В базу данной версии не включены Крым и Калинингад


Установка 
---------------------

1. Скопировать папку с плагином в дирректорию плагинов Wordpress (wp-content/plugins), перейти в админку и активировать.
2. Скопировать папку с плагином на локальный диск, перейти в админку Внешний вид -> Плагины, выбрать пункт -  добавить новый, выбрать папку с плагином на локальном диске, загрущить плагин, активировать.

Использование
----------------------

1. Функция cr_ip_region_form()

   Выводит инпут для ввода IP адреса и кнопку для отправки, проверка осуществяется с помощю Ajax запроса, без перезагрузки страницы. Если инпут пустой функция получит IP адрес текущего пользователя, если в инпут введен IP в функцию будет передан он, в случае некорректного ввода IP будет предложено ввести его повторно.
   
   В результате работы функция вернет Регион и Город к которым пенадлежит полученый IP, если  переданный IP не относится к пулу адресов из России, или его не окажется в базе функция вернет соответствующее сообщение.
    
	Форму можно вывести несколькими способами:
	* c помощю шорткода `[cr_ip_form]`  вставив его в контент страницы или виджета
	* c помощю фцнкции `<?php echo do_shortcode( '[cr_ip_form]' ); ?>` - вставив ее в необходимое место шаблона вывода
	* c помощю конструкции `<?php if ( function_exists('cr_ip_region_form') ) cr_ip_region_form() ; ?>` - вставив ее в необходимое место шаблона вывода
	
2. Функция get_conwert_ip_too_region()
	     
	Возвращает массив вида `Array ( [city] => Город, [city_id] => ID города, [region] => Регион, [region_id] => ID региона )`
		 
	Функция имеет необязательный параметр `$ip` если он не установлен, работать будет с IP текущего посетителя.
	
	Пример использования:
	
	```php
	<?php  if ( function_exists('get_conwert_ip_too_region') )  {
				$ip_array = get_conwert_ip_too_region(); // получаем массив с данными об IP
				$city_id = $ip_array[city_id];
  				if( $city_id ==  23541 ) { //где  23541 - ID Москвы
					// выводим что-то для Москвы
				} else {
					// выводим что-то для Остальных Городов
				}
			} 
	?>
	```

[Демо](http://wordpress-creative.com/cr-region-ip-demo/)
_____________________________________________________
