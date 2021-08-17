---
title: Specificare il file binario da avviare | Microsoft Docs
description: Informazioni su come immettere informazioni nella finestra di dialogo Pagine <Target> delle proprietà per profilare i file binari, ad esempio DLL.
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
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ec3a2355f6539472a2079bb0988bed1508c858303d9aee2c40e86b0f49e6531b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396474"
---
# <a name="how-to-specify-the-binary-to-start"></a>Procedura: Specificare l'avvio del file binario

Per profilare i file binari, ad esempio le DLL, è necessario immettere informazioni nella **\<Target> finestra di dialogo Pagine delle** proprietà. Queste informazioni indicano dove il progetto DLL può trovare l'applicazione chiamante.

1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul file binario di destinazione e quindi scegliere **Proprietà**.

2. Nella finestra di dialogo **Pagine delle proprietà** fare clic sulle proprietà di **Avvio**.

3. Selezionare la casella di controllo **Eseguire l'override delle impostazioni progetto**.

4. Nella casella di testo **Eseguibile da avviare** specificare il percorso del file.

5. Nella casella di testo **Argomenti** specificare gli argomenti necessari per avviare l'applicazione.

6. Nella casella di testo **Directory di lavoro** specificare il percorso della directory.

7. Fare clic su **OK**.

## <a name="see-also"></a>Vedi anche

[Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
