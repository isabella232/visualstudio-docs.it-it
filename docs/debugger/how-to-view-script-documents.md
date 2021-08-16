---
title: Visualizzare documenti script | Microsoft Docs
description: Informazioni su come visualizzare documenti script sul lato server JavaScript in Visual Studio usando Esplora soluzioni.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: db8d6ab713b745e63c2ab419fbb6d134a2e0284b521e9633cdda45185e1e3505
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378658"
---
# <a name="how-to-view-script-documents-javascript"></a>Procedura: Visualizzare documenti script (JavaScript)

I file script sul lato server sono visibili in Esplora soluzioni. I file script sul lato client sono visibili solo in modalità di debug o in modalità interruzione. I file script sul lato client vengono visualizzati nel **nodo Documenti script.**

Per alcuni tipi di applicazione che generano pagine in modo dinamico, è più facile accedere alla modalità di interruzione ed eseguire il debug quando si imposta un punto di interruzione da un documento script caricato nel browser. Analogamente, è possibile aggiungere l'istruzione `debugger` da un documento di script caricato per accedere alla modalità di interruzione. Questo articolo illustra come visualizzare questi documenti.

> [!NOTE]
> Prima di [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] , i file script sul lato client generati dallo script sul lato server sono stati aperti nella finestra Esplora script.

### <a name="to-view-a-server-side-script-document"></a>Per visualizzare un documento script sul lato server

1. In **Esplora soluzioni** aprire il **\<Website Pathname>** nodo.

2. Fare doppio clic sul file script che si desidera visualizzare.

     Il file script sul lato server verrà aperto in una finestra di origine.

### <a name="to-view-a-client-side-script-document"></a>Per visualizzare un documento script sul lato client

1. In **Esplora soluzioni** aprire il nodo **Documenti script**.

2. Fare doppio clic sul file script che si desidera visualizzare.

     Il file script sul lato client verrà aperto in una finestra di origine.

## <a name="see-also"></a>Vedi anche
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)