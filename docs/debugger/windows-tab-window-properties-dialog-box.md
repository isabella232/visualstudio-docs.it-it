---
title: Finestra di dialogo Proprietà finestra, scheda di Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce1015741b2a1e7ba1608eea7f198b726e808f7f
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696844"
---
# <a name="windows-tab-window-properties-dialog-box"></a>Scheda Finestre, finestra di dialogo Proprietà finestra
Usare la **Windows** pressione di tab per visualizzare informazioni sulle finestre correlate per la finestra selezionata. Per visualizzare il [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo per il [Windows Vista](../debugger/windows-view.md) finestra. Selezionare qualsiasi nodo finestra nell'albero e quindi scegliere **delle proprietà** dalle **visualizzazione** menu.

 Le impostazioni seguenti sono disponibili sul **Windows** scheda:

|Voce|Description|
|-----------|-----------------|
|**Finestra successiva**|L'handle della finestra di pari livello successiva nella stessa sequenza (Z order) mostrata nella visualizzazione struttura ad albero della finestra ("none" Se non vi è alcuna finestra successiva). Scegliere questa voce per visualizzare le proprietà della finestra successiva.|
|**Finestra precedente**|L'handle della finestra di pari livello precedente nella stessa sequenza (Z order) mostrata nella visualizzazione struttura ad albero della finestra ("none" Se non vi è alcuna finestra precedente). Scegliere questa voce per visualizzare le proprietà della finestra precedente.|
|**Finestra padre**|Handle della finestra padre della finestra ("none" Se non esiste alcun padre). Scegliere questa voce per visualizzare le proprietà della finestra padre.|
|**Primo elemento figlio**|Handle della finestra della finestra prima figlio, nella sequenza (Z order) mostrato nella visualizzazione struttura ad albero della finestra ("none" Se non esistono alcuna finestra figlio). Selezionare questo valore per visualizzare le proprietà della prima finestra figlio.|
|**Finestra proprietaria**|Handle della finestra proprietaria della finestra corrente. Finestra principale di un'applicazione è in genere proprietario finestre di dialogo modale del sistema, ad esempio ("none" Se non vi è alcun proprietario). Scegliere questa voce per visualizzare le proprietà della finestra proprietaria.|