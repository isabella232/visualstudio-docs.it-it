---
title: Specificare il file binario da avviare | Microsoft Docs
description: Informazioni su come immettere le informazioni nella finestra <Target> di dialogo Pagine delle proprietà per profilare file binari, ad esempio dll.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 715c92a26ae33a4e909ec737c866be1cdc15251e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721840"
---
# <a name="how-to-specify-the-binary-to-start"></a>Procedura: Specificare l'avvio del file binario

Per profilare i file binari, ad esempio le dll, è necessario immettere le informazioni nella finestra di dialogo **\<Target> pagine delle proprietà** . Queste informazioni indicano dove il progetto DLL può trovare l'applicazione chiamante.

1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul file binario di destinazione e quindi scegliere **Proprietà**.

2. Nella finestra di dialogo **Pagine delle proprietà** fare clic sulle proprietà di **Avvio**.

3. Selezionare la casella di controllo **Eseguire l'override delle impostazioni progetto**.

4. Nella casella di testo **Eseguibile da avviare** specificare il percorso del file.

5. Nella casella di testo **Argomenti** specificare gli argomenti necessari per avviare l'applicazione.

6. Nella casella di testo **Directory di lavoro** specificare il percorso della directory.

7. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

[Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
