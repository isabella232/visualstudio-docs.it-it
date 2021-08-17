---
title: Serializzare le informazioni sui simboli | Microsoft Docs
description: Informazioni su come serializzare i simboli necessari per analizzare l'applicazione e su come la serializzazione dei simboli aggiunge simboli al file con estensione vsp.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4ebb19f1bbd2c157f3814be3d52809c5f4edb4440f494b4575ec1289c0b3cc7f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231107"
---
# <a name="how-to-serialize-symbol-information"></a>Procedura: Serializzare le informazioni sui simboli
È possibile serializzare i simboli necessari per analizzare l'applicazione. Con la serializzazione dei simboli vengono aggiunti simboli al file con estensione *vsp*. L'aggiunta di informazioni sui simboli nel file con estensione *vsp* consente ad altri utenti di analizzare un rapporto di prestazioni senza dover accedere ai simboli originali. Se i simboli non vengono serializzati, sarà necessario disporre dei file *exe* e *pdb* originali instrumentati per analizzare il file *vsp*.

### <a name="to-automatically-serialize-symbol-information"></a>Per serializzare automaticamente le informazioni sui simboli

1. Scegliere **Opzioni** dal menu **Strumenti**.

     Verrà visualizzata la finestra di dialogo **Opzioni**.

2. Fare clic su **Strumenti per le prestazioni**.

3. In **Impostazione generale** selezionare **Serializzare automaticamente le informazioni sui simboli**.

## <a name="see-also"></a>Vedi anche
- [Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
- [Procedura: Fare riferimento Windows informazioni sui simboli](../profiling/how-to-reference-windows-symbol-information.md)
- [Procedura: Salvare file di rapporto analizzati](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
