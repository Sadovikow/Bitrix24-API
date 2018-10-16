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
	

### bitrix:intranet.user.selector.new

> Выбор пользователей

```php
$APPLICATION->IncludeComponent(
'bitrix:intranet.user.selector.new',
'',
array(
	'MULTIPLE' => 'N',
	//'NAME' => ,
	//'INPUT_NAME' => ,
	//'POPUP' => 'Y',
	//'INPUT_NAME' => "estimate_contact",
	'INPUT_NAME_STRING' => "estimate_contact_h",
	'INPUT_NAME_SUSPICIOUS' => "estimate_contact_h",
	'TEXTAREA_MIN_HEIGHT' => 30,
	'TEXTAREA_MAX_HEIGHT' => 60,
	//'INPUT_VALUE' => $thisEstimate['CONTACT'],
	//'EXTERNAL' => 'A',
	'SOCNET_GROUP_ID' => ($arParams["TASK_TYPE"] == "group" ? $arParams["OWNER_ID"] : "")

),
null,
array('HIDE_ICONS' => 'Y')
);
```
