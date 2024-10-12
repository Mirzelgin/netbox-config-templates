# netbox-config-templates
Коллекция шаблонов конфигурации для netbox на Jinja2. Почитать можно в официальном руководстве netbox [Configuration Templates](https://netboxlabs.com/docs/netbox/en/stable/models/extras/configtemplate/)

# Список шаблонов
## Mikrotik
- [mikrotik-base](#mikrotik-base)


# Описание шаблонов
## mikrotik-base
Реализует базовую конфигурацию интерфесов, bridge, vlan и ip-адресов. Особенности наполнения конфигурации устройств:
- comment - комментарии добавляются как есть, при наличии проблем с отображением вашего языка рекомендуется использовать английский
- interface bridge - создаётся из интерфеса типа *bridge*
- interface bridge - `vlan-filtering=yes` устанавливается только если *802.1Q Mode* установлен *tagged* или *tagged-all*
- interface bridge - *tagged-all* пока не реализован, непонятно какие vlan в этом режиме должны добавляться на устройство, которые привязанные к текущему сайту устройства или добавлены в указанную группу vlan
- interface vlan - создаются из интерфейсов типа *virtual* и прикрепляются к своему родительскому интерфесу
- interface vlan - у интерфеса обязательно *802.1Q Mode* должен быть установлен *access* и указан vlan
- bridge port - интерфесы в bridge добавляются если он у них установлен
- bridge vlan - vlan создаются из списка *tagged_vlan* на интерфесе
- bridge vlan - интерфесы добавляются если у них явно указан vlan и *802.1Q Mode* равен *tagged* или *untagged*
- ip address - IP-адреса добавляются как есть