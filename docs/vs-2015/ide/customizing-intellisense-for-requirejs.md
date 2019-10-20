---
title: Personalizzazione di IntelliSense per RequireJS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 279ac7737460c90f86918ae673e8f64ef1215546
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665887"
---
# <a name="customizing-intellisense-for-requirejs"></a>Personalizzazione di IntelliSense per RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partire da Visual Studio 2013 Update 4 è previsto il supporto del noto caricatore modulare e di file JavaScript RequireJS. RequireJS consente più facilmente di definire le dipendenze tra i moduli di codice e di caricare dinamicamente i moduli solo quando è necessario. Quando si scrive il codice JavaScript che usa RequireJS, verranno forniti dei suggerimenti di IntelliSense per i moduli a cui è stato fatto riferimento dalla definizione del modulo o mediante le chiamate a `require()` dall'interno del codice.

 Per impostazione predefinita, Visual Studio supporta una configurazione di base per supportare RequireJS, ma è consigliabile definire delle impostazioni di configurazione personalizzate (ovvero, definire gli alias per le librerie). Questo argomento descrive le diverse modalità con cui è possibile personalizzare Visual Studio per usare una configurazione univoca del progetto.

 Questo argomento descrive come:

- Personalizzare RequireJS in progetti ASP.NET

- Personalizzare RequireJS in progetti JSProj, che vengono usati per compilare app Apache Cordova, app Windows Store e app HTML LightSwitch

## <a name="customize-requirejs-in-aspnet-projects"></a>Personalizzare RequireJS in progetti ASP.NET
 Il supporto per RequireJS viene abilitato automaticamente quando il file JavaScript corrente fa riferimento a un file denominato require.js. Per altre informazioni, vedere la sezione Determinazione del contesto di IntelliSense in [IntelliSense per JavaScript](../ide/javascript-intellisense.md). Nei progetti ASP.NET, per fare riferimento a require.js, si usa generalmente una direttiva /// \<reference/> all'interno di un file _references.js.

### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Configurare l'attributo data-main in un progetto ASP.NET
 Per simulare in modo accurato il funzionamento dell'app quando viene eseguita, l'editor JavaScript deve sapere il file da caricare per primo durante la configurazione di require.js. Questo viene in genere configurato nel file HTML dell'applicazione usando l'attributo `data-main` nell'elemento di script che fa riferimento a require.js, come illustrato di seguito.

```html
<script src="js/require.js" data-main="js/app.js"></script>
```

 In questo esempio, lo script a cui fa riferimento data-main (js/app.js) viene caricato immediatamente dopo require.js. Il file che viene caricato immediatamente rappresenta la risorsa migliore in cui configurare l'utilizzo di RequireJS (tramite `require.config()`). Per indicare all'editor JavaScript il file da usare per `data-main` nell'applicazione, aggiungere un attributo `data-main`, quindi modificare una direttiva ///\<reference/> che fa riferimento a require.js nell'applicazione. È possibile ad esempio usare la direttiva seguente:

```javascript
/// <reference path="js/require.js" data-main="js/app.js" />
```

### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Configurare la pagina iniziale dell'applicazione in un progetto ASP.NET
 Quando viene eseguita l'app, RequireJS presuppone che i percorsi relativi dei file (ad esempio, ".. \\ "percorsi) sono relativi al file HTML che ha caricato la libreria require. js. Quando si scrive il codice nell'editor di Visual Studio per un progetto ASP.NET, questa pagina iniziale è sconosciuta e sarà necessario indicare all'editor la pagina iniziale da usare quando si usano i percorsi relativi dei file. A tale scopo, aggiungere un attributo `start-page` alla direttiva /// \<reference/>.

```javascript
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />
```

 L'attributo `start-page` specifica l'URL della pagina come verrà visualizzata in un browser quando si esegue l'app.

## <a name="customize-requirejs-in-jsproj-projects"></a>Personalizzare RequireJS in progetti JSProj
 I progetti JSProj (file di progetto che terminano con l'estensione jsproj) vengono usati per la compilazione delle app per Apache Cordova, le app Windows Store basate su HTML o le app HTML LightSwitch. A differenza dei progetti ASP.NET, questi progetti leggono i riferimenti ai file con estensione js dai file HTML che esistono nel progetto. Per questo motivo, quando si modifica JavaScript in un progetto JSProj, si noterà che il supporto per RequireJS viene abilitato se al file JavaScript che si sta modificando viene fatto riferimento in un altro file HTML che fa anche riferimento a require.js.

 I passaggi di personalizzazione necessari per i progetti ASP.NET non sono richiesti per un file di progetto JSProj. Ciò significa che i file di script usati dall'attributo `data-main` nel tag di script che fa riferimento a require.js vengono caricati automaticamente per configurare require.js. Il file HTML che fa riferimento a require.js viene usato anche come pagina iniziale per l'applicazione.

## <a name="see-also"></a>Vedere anche
 [IntelliSense per JavaScript](../ide/javascript-intellisense.md)
