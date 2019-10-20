---
title: Creare commenti JSDoc per IntelliSense per JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b974f3450b88ab22e58e284881f270c1b3d72298
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619266"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Creare commenti JSDoc per IntelliSense per JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense in Visual Studio visualizza le informazioni aggiunte a uno script tramite i commenti JSDoc standard. È possibile usare i commenti JSDoc per fornire informazioni sugli elementi di codice, come funzioni, campi e variabili.

## <a name="jsdoc-comment-tags"></a>Tag di commento JSDoc
 I tag di commento JSDoc standard elencati di seguito vengono usati da IntelliSense per visualizzare informazioni sul codice.

|  Tag JSDoc   |                       Sintassi                        |                                                     Note                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *descrizione*              |                                   Specifica una funzione o un metodo deprecato.                                   |
| @description |             @description *descrizione*              |                              Specifica la descrizione di una funzione o di un metodo.                               |
|    @param    | <em>descrizione</em> @param {*Type*} *parameterName* | Specifica le informazioni relative a un parametro in una funzione o un metodo.<br /><br /> TypeScript supporta anche @paramTag. |
|  @property   |          @property {*type*} *propertyName*          |   Specifica le informazioni, inclusa una descrizione, relative a un campo o a un membro definito per un oggetto.    |
|   @returns   |                  @returns {*type*}                  |           Specifica un valore restituito.<br /><br /> Per TypeScript, usare @returnType anziché @returns.           |
|   @summary   |               @summary *descrizione*                |                   Specifica la descrizione di una funzione o di un metodo (uguale a @description).                   |
|    @type     |                   @type {*type*}                    |                                Specifica il tipo di una costante o di una variabile.                                |
|   @typedef   |         @typedef {*type*} *customTypeName*          |                                            Specifica un tipo personalizzato.                                            |

### <a name="examples"></a>Esempi
 Nell'esempio seguente viene illustrato l'uso dei tag @description, @param e @return JSDoc per una funzione denominata `getArea`.

```javascript
/** @description Determines the area of a circle that has the specified radius parameter.
 * @param {number} radius The radius of the circle.
 * @return {number}
 */
function getArea(radius) {
    var areaVal;
    areaVal = Math.PI * radius * radius;
    return areaVal;
}
```

 Nell'esempio precedente IntelliSense mostra le informazioni su descrizione, parametri e valori restituiti quando si digita la parentesi di apertura per `getArea`.

 ![Informazioni IntelliSense per una funzione](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")

 Nell'esempio seguente viene illustrato come utilizzare il tag @typedef con il tag @property.

```javascript
/**
  * @typedef {object} Weather
  * @property {string} current The current weather.
  */
function getForecast(Weather) {
}

var w = new Weather();
```

 Nell'esempio seguente viene illustrato l'uso dei tag @type JSDoc. Come illustra questo esempio, gli asterischi singoli (*) che seguono la coppia di asterischi iniziale (\*\*) non sono obbligatori.

```javascript
/**
    @type {string}
*/
const RED = 'FF0000';

```

 Nell'esempio seguente viene illustrato come utilizzare il @deprecated Tag JSDoc.

```javascript
/**
 * @deprecated since version 2.0
 */
function old() {
}
```
