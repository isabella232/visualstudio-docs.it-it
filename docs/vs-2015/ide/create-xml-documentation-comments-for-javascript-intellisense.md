---
title: Creare commenti in formato documentazione XML per IntelliSense per JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code comments, JavaScript IntelliSense
- XML documentation comments, JavaScript IntelliSense
- documentation comments [JavaScript]
- IntelliSense [JavaScript], XML documentation comments
ms.assetid: a27f5b50-9807-436f-a0cf-6f3137ecbaf0
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3801fb58f09ac70c26e21304957e31f7b3ec4ddc
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2018
ms.locfileid: "48881020"
---
# <a name="create-xml-documentation-comments-for-javascript-intellisense"></a>Creare commenti in formato documentazione XML per IntelliSense per JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [documentazione di Visual Studio 2017](/visualstudio/).  
  
*Commenti in formato documentazione XML* sono JavaScript commenti aggiungere uno script per fornire informazioni sugli elementi di codice, ad esempio variabili, funzioni e campi. In Visual Studio, queste descrizioni di testo vengono visualizzate con IntelliSense quando si fa riferimento la funzione di script.  
  
 In questo argomento fornisce un'esercitazione di base sull'uso di commenti in formato documentazione XML. Per informazioni sull'uso di altri elementi, ad esempio [ \<var >](../ide/var-javascript.md) e [ \<valore >](../ide/value-javascript.md)e per altri esempi di codice, vedere [commenti in formato documentazione XML ](../ide/xml-documentation-comments-javascript.md). Per informazioni su come fornire le informazioni di IntelliSense per una richiamata asincrona, ad esempio un `Promise`, vedere [ \<restituisce >](../ide/returns-javascript.md).  
  
> [!NOTE]
>  I commenti della documentazione XML sono disponibili solo dai file, dagli assembly e dai servizi di riferimento.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-function"></a>Per creare i commenti della documentazione XML per una funzione JavaScript  
  
-   Nella funzione, aggiungere [ \<riepilogo >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), e [ \<restituisce >](../ide/returns-javascript.md) elementi e far precedere ogni elemento con tre barre (/ / /).  
  
    > [!NOTE]
    >  Ogni elemento deve essere su una singola riga.  
  
     Nell'esempio seguente viene illustrata una funzione JavaScript.  
  
    ```javascript  
    function getArea(radius)  
    {  
        /// <summary>Determines the area of a circle that has the specified radius parameter.</summary>  
        /// <param name="radius" type="Number">The radius of the circle.</param>  
        /// <returns type="Number">The area.</returns>  
        var areaVal;  
        areaVal = Math.PI * radius * radius;  
        return areaVal;  
    }  
    ```  
  
-   Per visualizzare i commenti della documentazione XML, digitare il nome e la parentesi di apertura di una funzione contrassegnata con commenti della documentazione XML, come nell'esempio seguente:  
  
    ```javascript  
    var areaVal = getArea(  
    ```  
  
     Quando si digita la parentesi di apertura della funzione che contiene i commenti della documentazione XML, Editor di codice Usa IntelliSense per visualizzare le informazioni che sono definite nei commenti della documentazione XML.  
  
### <a name="to-create-xml-documentation-comments-for-a-javascript-field"></a>Per creare commenti in formato documentazione XML per un campo di JavaScript  
  
-   In una definizione di funzione o oggetto costruttore, aggiungere un [ \<campo >](../ide/field-javascript.md) elemento preceduto da tre barre (/ / /).  
  
     L'esempio seguente illustra l'uso del `<field>` elemento in una funzione del costruttore. Per altri esempi, vedere [ \<campo >](../ide/field-javascript.md).  
  
    ```javascript  
    function Engine() {  
        /// <field name='HorsePower' type='Number'>The engine's horsepower.</field>  
        this.HorsePower = 150;  
    }  
    ```  
  
-   Per visualizzare i commenti della documentazione XML, creare un oggetto usando il costruttore di funzione contrassegnata con commenti della documentazione XML, come nell'esempio seguente.  
  
    ```javascript  
    var eng = new Engine();  
    ```  
  
-   Nella riga successiva, digitare il nome dell'oggetto e un punto per visualizzare le informazioni di IntelliSense per il campo.  
  
    ```javascript  
    eng.  
    ```  
  
### <a name="to-create-xml-documentation-comments-for-an-overloaded-function"></a>Per creare i commenti della documentazione XML per una funzione in overload  
  
1.  Nella funzione, aggiungere un [ \<firma >](../ide/signature-javascript.md) (elemento) per ogni overload. In tali elementi, aggiungere altri elementi, ad esempio `<summary>`, `<param>`, e `<returns>`, che precedono ogni elemento con tre barre (/ / /).  
  
     L'esempio seguente illustra una funzione JavaScript in overload. In questo esempio, gli overload limitarsi al tipo di parametro.  
  
    ```javascript  
    function calc(a) {  
        /// <signature>  
        /// <summary>Function summary 1.</summary>  
        /// <param name="a" type="Number">A number.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        /// <signature>  
        /// <summary>Function summary 2.</summary>  
        /// <param name="a" type="String">A string.</param>  
        /// <returns type="Number" />  
        /// </signature>  
        return a;  
    }  
    ```  
  
2.  Per visualizzare i commenti della documentazione XML, digitare il nome e la parentesi di apertura della funzione che è contrassegnata con i commenti della documentazione XML, come nell'esempio seguente:  
  
    ```javascript  
    calc(  
    ```  
  
### <a name="to-create-localized-intellisense"></a>Per creare IntelliSense localizzati  
  
1.  Creare un file XML contenente i commenti della documentazione in formato OpenAjax MessageBundle.  
  
    > [!IMPORTANT]
    >  MessageBundle è il formato consigliato. Questo formato non è supportato in Microsoft Ajax o in file con estensione winmd. Per informazioni sull'utilizzo l'alternativa `VSDoc` formato, vedere [ \<loc >](../ide/loc-javascript.md).  
  
     Nell'esempio seguente visualizza il contenuto in un file sidecar che contiene le informazioni IntelliSense localizzate. Si tratta di un file XML che si trova in una cartella di impostazioni cultura specifiche, ad esempio JA. La cartella deve essere nello stesso percorso del file. js che contiene il `<loc>` elemento. Il nome file del file XML deve corrispondere il `filename` specificato nel parametro di `<loc>` elemento.  
  
    ```  
    <messagebundle>  
      <msg name="1">A class that represents a rectangle</msg>  
      <msg name="2">The length of the rectangle</msg>  
      <msg name="3">The height of the rectangle</msg>  
    </messagebundle>  
  
    ```  
  
2.  Nel file con estensione js aggiungere il codice seguente. Il `<loc>` elemento deve essere dichiarato prima di qualsiasi script e segue le stesse regole di utilizzo come il `<reference>` elemento. Per altre informazioni, vedere [IntelliSense per JavaScript](../ide/javascript-intellisense.md) e [ \<loc >](../ide/loc-javascript.md).  
  
    ```javascript  
    /// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
    ```  
  
3.  Nel file con estensione js, aggiungere gli elementi di documentazione di XML e descrizioni predefinite. Impostare il `locid` corrispondere i corrispondenti valori di attributo `name` valori degli attributi dal file sidecar. Le descrizioni predefinite verranno sostituite in base a informazioni IntelliSense localizzati, se disponibile.  
  
    ```javascript  
    function add(a,b)   
    {  
        /// <summary locid='1'>description</summary>  
        /// <param name='a' locid='2'>parameter a description</param>  
        /// <param name='b' locid='3'>parameter b description</param>  
    }  
  
    ```  
  
4.  Per visualizzare i commenti della documentazione XML, digitare il nome e la parentesi di apertura della funzione, come nell'esempio seguente:  
  
    ```javascript  
    add(  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [IntelliSense per JavaScript](../ide/javascript-intellisense.md)   
 [Commenti relativi alla documentazione XML](../ide/xml-documentation-comments-javascript.md)   
 [NIB: Procedura dettagliata: JavaScript IntelliSense in ASP.NET](http://msdn.microsoft.com/en-us/4f6e0cc2-7f48-4dbf-abb0-7fb743a2d05b)



