---
title: Automatizzare l'installazione con un file di risposta
description: Informazioni su come creare un file di risposta JSON che consente di automatizzare l'installazione di Visual Studio
ms.date: 08/14/2017
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58c8d580ace576f7b2a4512e5bc91f83529fba77
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939580"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Come definire impostazioni in un file di risposta

Gli amministratori che distribuiscono Visual Studio possono specificare un file di risposta usando il parametro `--in`, come nell’esempio che segue:

```cmd
vs_enterprise.exe --in customInstall.json
```

I file di risposta sono costituiti da file [JSON](http://json-schema.org/) i cui contenuti riflettono gli argomenti della riga di comando.  In generale, se un parametro della riga di comando non accetta argomenti (ad esempio, `--quiet`, `--passive` e così via), il valore nel file di risposta deve essere true o false.  Se invece accetta un argomento (ad esempio, `--installPath <dir>`), il valore nel file di risposta deve essere una stringa.  Se accetta un argomento e può apparire più di una volta nella riga di comando (ad esempio, `--add <id>`), deve essere una matrice di stringhe.

Parametri specificati nelle impostazioni di sostituzione della riga di comando dal file di risposta, tranne quando i parametri hanno più input (ad esempio, `--add`). Quando si dispone di più input, gli input nella riga di comando specificati vengono uniti con le impostazioni dal file di risposta.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Impostazione di una configurazione predefinita per Visual Studio

Se è stata creata una cache di layout di rete con l'opzione `--layout`, nel layout viene creato un file `response.json` iniziale. Se si crea un layout parziale, il file di risposta include le lingue e i carichi di lavoro inclusi nel layout.  L’esecuzione automatica dell'installazione da questo layout utilizza questo file response.json che seleziona i carichi di lavoro e i componenti inclusi nel layout.  Gli utenti possono comunque selezionare o deselezionare i carichi di lavoro nel programma di installazione dell'interfaccia utente prima di installare Visual Studio.

Gli amministratori che creano un layout possono modificare il file `response.json` nel layout per controllare le impostazioni predefinite che gli utenti visualizzeranno durante l'installazione di Visual Studio dal layout.  Se, ad esempio, un amministratore vuole che, per impostazione predefinita, vengano installati specifici carichi di lavoro e componenti, per aggiungerli può configurare il file `response.json`.

Se l'installazione di Visual Studio viene eseguita da una cartella di layout, viene _automaticamente_ usato il file di risposta nella cartella di layout.  Non è necessario usare l’opzione `--in`.

È possibile aggiornare il file `response.json` creato in una cartella di layout offline per definire l'impostazione predefinita per gli utenti che eseguono l'installazione da questo layout.

> [!WARNING]
> È essenziale lasciare invariate le proprietà esistenti definite al momento della creazione del layout.

Il file base `response.json` in un layout deve avere un aspetto simile all'esempio seguente, ad eccezione del fatto che si includa il valore per il prodotto e il canale che si desidera installare:

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

Quando si crea o aggiorna un layout, viene creato anche un file response.template.json.  Questo file contiene tutto il carico di lavoro, un componente e degli ID che può essere utilizzato.  Questo file viene fornito come un modello per il quale è possibile includere tutto in un'installazione personalizzata.  Gli amministratori possono utilizzare questo file come punto di partenza per un file di risposta personalizzata.  Basta rimuovere gli ID per le operazioni che non si desidera installare e salvarlo in un file di risposta.  Non personalizzare il file response.template.json o le modifiche andranno perse ogni volta che viene aggiornato il layout.

## <a name="example-layout-response-file-content"></a>Esempio di contenuto del file di risposta del layout

Il seguente esempio viene installato Visual Studio Enterprise con sei carichi di lavoro e componenti comuni e con interfaccia utente sia in inglese che in francese. È possibile usare questo esempio come modello, semplicemente sostituendo i carichi di lavoro e i componenti con quelli che si vuole installare.

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md)
