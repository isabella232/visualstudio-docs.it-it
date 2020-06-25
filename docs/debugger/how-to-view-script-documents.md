---
title: Come visualizzare documenti script | Microsoft Docs
ms.date: 11/05/2019
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcd9823e414005a1711ddccf9d972da929090920
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348444"
---
# <a name="how-to-view-script-documents-javascript"></a>Procedura: visualizzare documenti script (JavaScript)

I file script sul lato server sono visibili in Esplora soluzioni. I file script sul lato client sono visibili solo in modalità di debug o in modalità interruzione. I file script sul lato client vengono visualizzati nel nodo **documenti script** .

Per alcuni tipi di applicazione che generano dinamicamente pagine, è più semplice attivare la modalità di interruzione ed eseguire il debug quando si imposta un punto di interruzione da un documento di script caricato nel browser. Analogamente, è possibile aggiungere l' `debugger` istruzione da un documento di script caricato per attivare la modalità di interruzioni. Questo articolo illustra come visualizzare questi documenti.

> [!NOTE]
> Prima di [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] , i file di script sul lato client generati da uno script sul lato server venivano visualizzati nella finestra Esplora script.

### <a name="to-view-a-server-side-script-document"></a>Per visualizzare un documento script sul lato server

1. In **Esplora soluzioni**aprire il **\<Website Pathname>** nodo.

2. Fare doppio clic sul file script che si desidera visualizzare.

     Il file script sul lato server verrà aperto in una finestra di origine.

### <a name="to-view-a-client-side-script-document"></a>Per visualizzare un documento script sul lato client

1. In **Esplora soluzioni** aprire il nodo **Documenti script**.

2. Fare doppio clic sul file script che si desidera visualizzare.

     Il file script sul lato client verrà aperto in una finestra di origine.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)