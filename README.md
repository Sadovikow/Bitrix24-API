# Bitrix24-API
Основные фичи Битрикс24 API, в том числе CRM

<h3>GetList Контактов из CRM на d7</h3>
```php
\Bitrix\Main\Loader::includeModule('crm');
$arFilter = array();
 $arSelect = array();
$dbFields = CCrmContact::GetList(array('DATE_CREATE' => 'DESC'), $arFilter, $arSelect, false);

while($arResult = $dbFields->Fetch()) 
{ 
	echo '<pre>';
	print_r($arResult); 
	echo '</pre>';
}
```
