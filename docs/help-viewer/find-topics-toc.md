---
title: Usare il sommario di Help Viewer in Visual Studio
description: Usare Microsoft Help Viewer per trovare gli argomenti nel sommario (sommario). Il sommario è un elenco espandibile che contiene tutti gli argomenti presenti nei libri installati.
ms.date: 11/02/2017
ms.topic: how-to
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer, table of contents filtering
- Help Viewer, Contents tab
- Contents tab [Help Viewer]
- table of contents filtering [Help Viewer]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a678b669ca0f389a79438185ffce605143ec71d0
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91879008"
---
# Procedura: Trovare argomenti nel sommario

Nella scheda **Contenuto** è possibile usare il sommario per trovare le informazioni. Il sommario è un elenco espandibile che contiene tutti argomenti dei libri installati. Per informazioni sull'accessibilità relative a come spostarsi nel sommario, vedere [Tasti di scelta rapida (Help Viewer)](../help-viewer/shortcut-keys.md).

> [!IMPORTANT]
> L'ambito degli argomenti disponibili nel sommario dipende dal filtro selezionato.

## Filtrare il sommario

È possibile filtrare il sommario per limitare l'ambito degli argomenti visualizzati nella scheda **contenuto** . I titoli vengono visualizzati nell'elenco solo se contengono la radice del termine specificato. Ad esempio, se si specifica la parola "risoluzione" come filtro, verranno visualizzati solo i titoli contenenti la parola "risolvere" o "risoluzione". I nodi i cui titoli non contengono il termine verranno compressi in un unico nodo con i puntini di sospensione (**...**).

1. Scegliere la scheda **Contenuto**.

2. Nella casella di testo **Filtra contenuti** immettere un termine.

> [!NOTE]
> Se l'esecuzione del filtro richiede molto tempo, è possibile visualizzare i risultati più rapidamente usando l'operatore di ricerca avanzata `title:`.

## Sincronizzare un argomento con il sommario

Se un argomento è stato aperto tramite l'indice o le funzionalità di ricerca full-text, è possibile determinarne la posizione all'interno del sommario sincronizzando quest'ultimo con la finestra dell'argomento.

1. Visualizzare un argomento.

2. Fare clic sul pulsante **Mostra argomento nel contenuto** nella barra degli strumenti oppure premere **CTRL**+**S**.

     Viene aperta la scheda **Contenuto** in cui viene visualizzata la posizione dell'argomento nel sommario.

## Vedere anche

- [Procedura: trovare argomenti nell'indice](../help-viewer/find-topics-index.md)
- [Procedura: Eseguire la ricerca di argomenti](../help-viewer/find-topics.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)