---
title: Creare commenti JSDoc per IntelliSense per JavaScript | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a0dadc81-3755-4a47-bcee-c1010819ff2a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f4d300651731b38b9b86421d36d9de169dc6464d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188779"
---
# <a name="create-jsdoc-comments-for-javascript-intellisense"></a>Creare commenti JSDoc per IntelliSense per JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliSense in Visual Studio visualizza le informazioni aggiunte a uno script tramite i commenti JSDoc standard. È possibile usare i commenti JSDoc per fornire informazioni sugli elementi di codice, come funzioni, campi e variabili.  

## <a name="jsdoc-comment-tags"></a>Tag di commento JSDoc  
 I tag di commento JSDoc standard elencati di seguito vengono usati da IntelliSense per visualizzare informazioni sul codice.  

|  Tag JSDoc   |                       Sintassi                        |                                                     Note                                                      |
|--------------|-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
| @deprecated  |              @deprecated *description*              |                                   Specifica una funzione o un metodo deprecato.                                   |
| @description |             @description *descrizione*              |                              Specifica la descrizione di una funzione o di un metodo.                               |
|    @param    | @param {*tipo*} *parameterName*<em>descrizione</em> | Specifica le informazioni relative a un parametro in una funzione o un metodo.<br /><br /> TypeScript supporta anche @paramTag. |
|  @property   |          @property {*type*} *propertyName*          |   Specifica le informazioni, inclusa una descrizione, relative a un campo o a un membro definito per un oggetto.    |
|   @returns   |                  @returns {*type*}                  |           Specifica un valore restituito.<br /><br /> Per TypeScript, usare @returnType invece di @returns.           |
|   @summary   |               @summary *description*                |                   Specifica la descrizione di una funzione o metodo (uguale a @description).                   |
|    @type     |                   @type {*type*}                    |                                Specifica il tipo di una costante o di una variabile.                                |
|   @typedef   |         @typedef {*type*} *customTypeName*          |                                            Specifica un tipo personalizzato.                                            |

### <a name="examples"></a>Esempi  
 L'esempio seguente illustra l'uso del @description, @param, e @return tag JSDoc per una funzione denominata `getArea`.  

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

 ![Informazioni di IntelliSense per una funzione](../ide/media/js-intellisense-jsdoc-comments.png "JS_IntelliSense_JSDoc_Comments")  

 Nell'esempio seguente viene illustrato come utilizzare il @typedef contrassegnare con il @property tag.  

```javascript  
/**  
  * @typedef {object} Weather  
  * @property {string} current The current weather.  
  */  
function getForecast(Weather) {  
}  

var w = new Weather();  
```  

 L'esempio seguente illustra l'uso del @type tag JSDoc. Come illustra questo esempio, gli asterischi singoli (*) che seguono la coppia di asterischi iniziale (\*\*) non sono obbligatori.  

```javascript  
/**  
    @type {string}  
*/  
const RED = 'FF0000';  

```  

 Nell'esempio seguente viene illustrato come utilizzare il @deprecated tag JSDoc.  

```javascript  
/**  
 * @deprecated since version 2.0  
 */  
function old() {  
}  
```
