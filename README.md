Tasas de impuestos de la UE de Magento
====================

A partir del 1 de enero de 2015, la normativa fiscal de la UE ha cambiado en materia fiscal. En algunos casos,
en lugar del cálculo de impuestos original,
donde el vendedor tomó la tasa impositiva de su propio país, el impuesto ahora debe basarse en el país de
el vendedor. La mayoría de estos casos se relacionan con las ventas de bienes o servicios digitales.
Dentro de Magento, esto simplemente significa que el impuesto se calcula utilizando tasas impositivas que difieren según la UE.
país. 

Este repositorio contiene un archivo `tax_rates_eu.csv` que se puede importar a la configuración del sistema Magento
para configurar las tasas de impuestos automáticamente.

## Uso Magento 1.x
Inicie sesión en su backend de Magento y vaya a `Ventas > Impuestos > Tasas de impuestos de importación/exportación`.
Use `Tasas de impuestos de exportación` para hacer una copia de seguridad de sus tasas anteriores. Use `Tasas de impuestos de importación` para cargar el archivo
`tax_rates_eu.csv` de este repositorio.

Tenga en cuenta que la primera fila del CSV está en inglés y necesitará que se cargue la configuración regional en inglés para este CSV.
para ser importado correctamente. Para permitir esto: cambie la configuración regional en la parte inferior de su panel de administración de Magento
a "Inglés (Estados Unidos)".

## Uso Magento 2.x
Inicie sesión en su backend de Magento y vaya a `Sistema > Tasas de impuestos de importación/exportación`.
Use `Tasas de impuestos de exportación` para hacer una copia de seguridad de sus tasas anteriores. Haga clic en `Examinar...` y seleccione el archivo descargado
`tax_rates_eu.csv` de este repositorio y haga clic en `Importar tasas impositivas`.

## Administrar tasas de impuestos automáticamente con la extensión Yireo TaxRatesManager
Periódicamente, las tasas de impuestos cambian. Cuando se trata de una tienda Magento concurrida, querrá cambiar las tasas de impuestos tan pronto como sea el momento, para evitar ventas después.
esa fecha con las tasas impositivas incorrectas. Aquí es donde nuestra extensión paga Yireo TaxRatesManager entra en escena. Garantiza que un determinado impuesto
las tasas se cambian correctamente en la fecha correcta.

Esta extensión comercial de Yireo en realidad hace uso de la información de este repositorio. El archivo `feeds.json` se utiliza para obtener una lista de posibles fuentes, mientras que
la convención de nomenclatura de los otros archivos CSV asegura que en una fecha específica cambien los archivos correctos. La extensión depende de cron para ejecutarse. También se envía
con una capacidad de corrección automática a través de cron y a través del backend: la opción de backend le permite obtener una vista previa de qué tipo de cambios se realizarán en una fecha específica.

- Extensión Yireo TaxRatesManager para Magento 1: https://www.yireo.com/software/magento-extensions/taxratesmanager
- Extensión Yireo TaxRatesManager para Magento 2: https://www.yireo.com/software/magento-extensions/taxratesmanager2

## Descargo de responsabilidad sobre la corrección
No somos contables. No pretendemos ser tenedores de libros. Si desea asegurarse de que estas tasas impositivas se apliquen a su propio
tienda o no, asegúrese de consultar a su contable local.

Tomamos la información de varios sitios de terceros como Wikipedia. La información puede ser incorrecta.
Si tiene un mejor recurso para basar este archivo CSV, háganoslo saber.

Este archivo ha sido probado hasta ahora en las siguientes versiones de Magento:
* Magento CE 1.9
* Magento CE 1.8
* Magento CE 2.0
* Magento CE 2.1
* Magento CE 2.2
* Magento CE 2.3

Lo más probable es que esto también funcione sin problemas en las versiones EE.

## Necesitamos ayuda
Necesitamos tu ayuda. Si descarga esta lista y encuentra un error, infórmenos (y a la comunidad)
Infórmate a través de info@yireo.com.

Más información está aquí:
- http://europa.eu/youreurope/business/vat-customs/buy-sell/
- http://www.vatlive.com/vat-rates/european-vat-rates/eu-vat-rates/
- https://github.com/yireo/Magento_EU_Tax_Rates/issues/url

## Pruebas
### Prueba de la funcionalidad de TaxRatesManager
Bifurque este repositorio de GitHub y luego agregue un archivo específico. Luego, vuelva a configurar su extensión TaxRatesManager para usar un
archivo CSV diferente.

### Prueba de cambios de impuestos en los archivos CSV
Para este repositorio de GitHub y agregue un archivo `diff` en la carpeta `diff` siguiendo el estándar de nomenclatura de otros archivos.
Por ejemplo, un archivo diff con el nombre de archivo `diff/tax_rates_eu_2020-07-01.diff`. También puede utilizar el guión
`bin/create_diff.sh` para generar este archivo basado en los cambios que ha realizado en `tax_rates_eu.csv`.

A continuación, ejecute el script `bin/apply_diff.sh`.
