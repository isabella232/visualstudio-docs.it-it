---
title: Personalizzazione di IntelliSense per RequireJS | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fbc4d9b85a3eb8e0fe5f3a890a76bae4695912e4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517320"
---
# <a name="customizing-intellisense-for-requirejs"></a>Personalizzazione di IntelliSense per RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [documentazione di Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
A partire da Visual Studio 2013 Update 4 è previsto il supporto del noto caricatore modulare e di file JavaScript RequireJS. RequireJS consente più facilmente di definire le dipendenze tra i moduli di codice e di caricare dinamicamente i moduli solo quando è necessario. Quando si scrive il codice JavaScript che usa RequireJS, verranno forniti dei suggerimenti di IntelliSense per i moduli a cui è stato fatto riferimento dalla definizione del modulo o mediante le chiamate a `require()` dall'interno del codice.  
  
 Per impostazione predefinita, Visual Studio supporta una configurazione di base per supportare RequireJS, ma è consigliabile definire delle impostazioni di configurazione personalizzate (ovvero, definire gli alias per le librerie). Questo argomento descrive le diverse modalità con cui è possibile personalizzare Visual Studio per usare una configurazione univoca del progetto.  
  
 Questo argomento descrive come:  
  
-   Personalizzare RequireJS in progetti ASP.NET  
  
-   Personalizzare RequireJS in progetti JSProj, che vengono usati per compilare app Apache Cordova, app Windows Store e app HTML LightSwitch  
  
## <a name="customize-requirejs-in-aspnet-projects"></a>Personalizzare RequireJS in progetti ASP.NET  
 Supporto per RequireJS viene abilitato automaticamente quando il file JavaScript corrente fa riferimento un file denominato Require. js (per altre informazioni, vedere la sezione determinazione del contesto di IntelliSense in [JavaScript IntelliSense](../ide/javascript-intellisense.md)). Nei progetti ASP.NET, che fanno riferimento a Require. js viene in genere eseguita usando un / / / \<riferimento / > direttiva all'interno di un file References.  
  
### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Configurare l'attributo data-main in un progetto ASP.NET  
 Per simulare in modo accurato il funzionamento dell'app quando viene eseguita, l'editor JavaScript deve sapere il file da caricare per primo durante la configurazione di require.js. Questo viene in genere configurato nel file HTML dell'applicazione usando l'attributo `data-main` nell'elemento di script che fa riferimento a require.js, come illustrato di seguito.  
  
```html  
<script src="js/require.js" data-main="js/app.js"></script>  
```  
  
 In questo esempio, lo script a cui fa riferimento data-main (js/app.js) viene caricato immediatamente dopo require.js. Il file viene caricato immediatamente è il modo migliore per configurare innanzitutto l'utilizzo di RequireJS (mediante `require.config()`). Per indicare quali file da utilizzare per l'editor JavaScript `data-main` nell'applicazione, aggiungere un' `data-main` dell'attributo e quindi modificare un / / / \<riferimento / > direttiva che fa riferimento a Require. js nell'applicazione. È possibile ad esempio usare la direttiva seguente:  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" />  
```  
  
### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Configurare la pagina iniziale dell'applicazione in un progetto ASP.NET  
 Quando si esegue l'app, RequireJS presuppone che relativo i percorsi dei file (ad esempio, ".. \\") sono relativi al file HTML che caricato la libreria Require. js. Quando si scrive il codice nell'editor di Visual Studio per un progetto ASP.NET, questa pagina iniziale è sconosciuta e sarà necessario indicare all'editor la pagina iniziale da usare quando si usano i percorsi relativi dei file. A questo scopo, aggiungere un `start-page` dell'attributo per / / / \<riferimento / > direttiva.  
  
```javascript  
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />  
```  
  
 L'attributo `start-page` specifica l'URL della pagina come verrà visualizzata in un browser quando si esegue l'app.  
  
## <a name="customize-requirejs-in-jsproj-projects"></a>Personalizzare RequireJS in progetti JSProj  
 I progetti JSProj (file di progetto che terminano con l'estensione jsproj) vengono usati per la compilazione delle app per Apache Cordova, le app Windows Store basate su HTML o le app HTML LightSwitch. A differenza dei progetti ASP.NET, questi progetti leggono i riferimenti ai file con estensione js dai file HTML che esistono nel progetto. Per questo motivo, quando si modifica JavaScript in un progetto JSProj, si noterà che il supporto per RequireJS viene abilitato se al file JavaScript che si sta modificando viene fatto riferimento in un altro file HTML che fa anche riferimento a require.js.  
  
 I passaggi di personalizzazione necessari per i progetti ASP.NET non sono richiesti per un file di progetto JSProj. Ciò significa che i file di script usati dall'attributo `data-main` nel tag di script che fa riferimento a require.js vengono caricati automaticamente per configurare require.js. Il file HTML che fa riferimento a require.js viene usato anche come pagina iniziale per l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IntelliSense per JavaScript](../ide/javascript-intellisense.md)



