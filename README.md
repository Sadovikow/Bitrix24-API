# Bitrix24-API
> Основные фичи Битрикс24 API, в том числе CRM

### GetList Контактов из CRM на d7

```php
if(\Bitrix\Main\Loader::includeModule('crm')):

	$arFilter = array();
	$arSelect = array();
	$dbFields = CCrmContact::GetList(array('DATE_CREATE' => 'DESC'), $arFilter, $arSelect, false);
	while($arResult = $dbFields->Fetch()) 
	{ 
		echo '<pre>';
		print_r($arResult); 
		echo '</pre>';
	}

endif;
```
	CCrmContact::GetList - Контакты
	CCrmCompany::GetList - Компании
	CCrmLead::GetList - Лиды
	CCrmDeal::GetList - Сделки



### Отправляем SMS при смене статуса заказа

Задача, **нужно добавить дополнительное уведомление по sms администратору о смене заказа.**

Заходим в /bitrix/php_interfaces/init.php(если его нет, то создаем). И пишем простой код. 

```php
AddEventHandler("sale", "OnSaleStatusOrder", "MyOnSaleStatusOrder");
function MyOnSaleStatusOrder($ID, $val)
{
   if (CModule::IncludeModule("rarus.sms4b"))
   {
      global $SMS4B;
      $text = "У заказа №".$ID." поменялся статус заказа";
      $adminPhoneNumber = "79999999999"; // Телефон администратора
      
      $SMS4B->SendSms($text, $adminPhoneNumber);
   }
}
```
