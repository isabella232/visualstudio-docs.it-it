---
title: Aggiornare un'app UWP | Microsoft Docs
description: Apportare modifiche al codice durante il debug e quindi aggiornare un'app UWP (Universal Windows Platform) usando JavaScript in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- JavaScript debugging, refreshing pages [UWP apps]
- debugging, refreshing pages [UWP apps]
- DOM Explorer, Refresh [UWP apps]
- Refresh [UWP apps]
ms.assetid: fd99ee60-fa94-46df-8b17-369f60bfd908
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- uwp
ms.openlocfilehash: 9beb9a96b64d9ad60e6aba1a407bdddb11f61ee1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122112503"
---
# <a name="refresh-a-uwp-app-in-visual-studio"></a>Aggiornare un'app UWP in Visual Studio

 È possibile apportare modifiche al codice durante il debug e quindi aggiornare un'app UWP usando JavaScript scegliendo il pulsante **Aggiorna** app Windows sulla barra degli **strumenti Debug.** Facendo clic su questo pulsante, l'app viene ricaricata senza arrestare e riavviare il debugger. La funzionalità di aggiornamento ti consente di modificare il codice HTML, CSS e JavaScript e visualizzare rapidamente i risultati. Questa funzionalità è supportata per le app UWP.

 L'aggiornamento non mantiene lo stato dell'app né riflette le seguenti modifiche nell'app:

- Modifiche al file manifesto del pacchetto, incluse le modifiche alle immagini specificato nel manifesto di pacchetto.

- Modifiche dei riferimenti, ad esempio l'aggiunta o la rimozione di un riferimento SDK, o le modifiche ai componenti Windows Runtime (file con estensione winmd).

- Modifiche delle risorse, ad esempio modifiche alle stringhe nei file con estensione resjson.

- Modifiche dei file di progetto che causano modifiche dei nomi di percorso, nuovi file di progetto e file eliminati.

- Modifiche delle proprietà di elementi e progetti, ad esempio modifiche al dispositivo di debug selezionato o modifiche all'azione del pacchetto per un file (nella finestra Proprietà).

> [!IMPORTANT]
> Quando modifichi i riferimenti, cambi il manifesto del pacchetto o apporti altre modifiche specificate nell'elenco precedente, devi arrestare e riavviare il debugger per aggiornare i file di origine HTML, CSS e JavaScript.

### <a name="to-refresh-an-app"></a>Per aggiornare un'app

1. Con il progetto UWP aperto in Visual Studio, selezionare **Computer locale** come destinazione di debug.

     ![Selezionare l'elenco di destinazione del debug](../debugger/media/js_select_target.png "JS_Select_Target")

3. Premi F5 per eseguire l'app in modalità debug.

4. Passa a Visual Studio.

5. Nel home page dell'app UWP modificare parte del codice HTML.

7. Fare clic **sul pulsante Aggiorna Windows'app,** simile al seguente: ![Aggiorna Windows'app.](../debugger/media/js_refresh.png "JS_Refresh") o premi F4.

8. Torna all'app. L'app viene ricaricata e il codice HTML aggiornato viene usato per eseguire il rendering dell'app.

## <a name="see-also"></a>Vedi anche
- [Guida introduttiva: Eseguire il debug di HTML e CSS](../debugger/quickstart-debug-html-and-css.md)