### links
- [AGCOM](https://geo.agcom.it/)
- [Reportistica](https://geo.agcom.it/reportistica/) delle consistenze dei punti geografici raggiunti dalla rete cablata
- Consistenze rilevate al [30/6/2025](https://geo.agcom.it/arcgis/sharing/rest/content/items/26857a93bc794ffea313ac956ecd99c0/data)  (rev. del 11/7/2025)
- Consistenze rilevate al [31/3/2025](https://geo.agcom.it/arcgis/sharing/rest/content/items/ceddc94230524fd688eaba5dc5af2bbf/data) (rev. del 7/5/2025)
- [ISTAT](https://www.istat.it/notizia/confini-delle-unita-amministrative-a-fini-statistici-al-1-gennaio-2018-2/) "Confini delle unità amministrative a fini statistici"
- Comuni [2025](https://www.istat.it/storage/cartografia/confini_amministrativi/non_generalizzati/2025/Limiti01012025.zip) (versione NON generalizzata)
- Comuni [2025](https://www.istat.it/storage/cartografia/confini_amministrativi/generalizzati/2025/Limiti01012025_g.zip) (versione generalizzata)
- [Model builder](https://docs.qgis.org/3.40/it/docs/user_manual/processing/modeler.html) o "Progettazione Modello"
- [Esportare](https://docs.qgis.org/3.40/it/docs/user_manual/processing/modeler.html#exporting-a-model-as-a-python-script) un modello come script Python
- Processing by [Python](https://docs.qgis.org/3.40/it/docs/user_manual/processing/scripts.html)


### Modelli path
- Linux: $HOME/.local/share/QGIS/QGIS3/profiles/default/processing/models
- Windows (Power Shell): $HOME\AppData\Roaming\QGIS\QGIS3\profiles\default\processing\models

### Utilizzo di variabili nelle espressioni
```
concat(@campo_di_comparazione, ' (differenza)')

if(length(attribute(@campo_di_comparazione)) > 0 AND length(attribute(concat('next_', @campo_di_comparazione))) > 0, to_int(attribute(concat('next_', @campo_di_comparazione))) - to_int(attribute( @campo_di_comparazione )), NULL)
```
