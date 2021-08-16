---
title: Windows Scheda, finestra di dialogo Proprietà finestra | Microsoft Docs
description: Usare la Windows di Windows proprietà per visualizzare le informazioni sulle finestre correlate alla finestra selezionata. Vedere questo articolo per le impostazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f13a9ee3f8b1ea245625b1734f4d7053e331228a29bdc4bcd78c49aafa34f7db
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378450"
---
# <a name="windows-tab-window-properties-dialog-box"></a>Scheda Finestre, finestra di dialogo Proprietà finestra
Usare la **Windows** per visualizzare informazioni sulle finestre correlate alla finestra selezionata. Per visualizzare la [finestra di dialogo Proprietà finestra](../debugger/window-properties-dialog-box.md), spostare lo stato attivo Windows [visualizzazione.](../debugger/windows-view.md) Selezionare qualsiasi nodo della finestra nell'albero, quindi **scegliere Proprietà** **dal** menu Visualizza.

 Nella scheda Windows sono disponibili **le impostazioni** seguenti:

|Voce|Descrizione|
|-----------|-----------------|
|**Finestra successiva**|Handle della finestra di pari livello successiva nella stessa sequenza (ordine Z) visualizzata nella visualizzazione albero della finestra ("none" se non è presente alcuna finestra successiva). Scegliere questa voce per visualizzare le proprietà della finestra successiva.|
|**Finestra precedente**|Handle della finestra di pari livello precedente nella stessa sequenza (ordine Z) visualizzata nella visualizzazione albero della finestra ("none" se non è presente alcuna finestra precedente). Scegliere questa voce per visualizzare le proprietà della finestra precedente.|
|**Finestra padre**|Handle della finestra padre di questa finestra ("none" se non è presente alcun elemento padre). Scegliere questa voce per visualizzare le proprietà della finestra padre.|
|**First Child**|Handle della prima finestra figlio di questa finestra, nella sequenza (ordine Z) visualizzata nella visualizzazione albero della finestra ("none" se non sono presenti finestre figlio). Scegliere questo valore per visualizzare le proprietà della prima finestra figlio.|
|**Finestra proprietaria**|Handle della finestra proprietaria di questa finestra. La finestra principale di un'applicazione è in genere proprietaria di finestre di dialogo modali di sistema, ad esempio ("none" se non è presente alcun proprietario). Scegliere questa voce per visualizzare le proprietà della finestra proprietaria.|