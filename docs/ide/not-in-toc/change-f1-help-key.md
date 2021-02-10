---
title: Modificare il tasto della Guida F1
description: Viene descritto come rimappare o rimuovere il mapping del tasto F1
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jmartens
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 30073b31fb98f604313c8de5d45687f3f768a374
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961690"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Modificare il tasto della Guida F1 in Visual Studio

Se si desidera utilizzare il tasto F1 per una funzione diversa rispetto al servizio Guida F1 o si desidera disabilitare la guida utilizzando F1, è possibile rimuovere o modificare il mapping delle chiavi.

> [!IMPORTANT]
> Se si desidera disabilitare la Guida F1 a causa di problemi di prestazioni, è consigliabile modificare temporaneamente il mapping delle chiavi, in modo da poter testare i miglioramenti apportati al servizio Guida sensibile al contesto negli aggiornamenti di Visual Studio. Nella maggior parte degli scenari F1 è un modo semplice per aprire le pagine di riferimento per le parole chiave e le API del linguaggio dall'editor di codice o per aprire le pagine della Guida associate agli elementi Windows o dell'interfaccia utente nell'IDE. Se viene disabilitato, viene disabilitato per tutti gli utilizzi da Visual Studio.

**Per disabilitare la Guida sensibile al contesto:**

1. In Visual Studio selezionare **strumenti**  >  **Opzioni**, quindi in **ambiente** selezionare **tastiera**.

1. Nella casella di testo **Mostra comandi contenenti** digitare **Help. F1** per filtrare la visualizzazione dei comandi.

   ![Disabilitare la Guida sensibile al contesto](../not-in-toc/media/disable-f1-help-key.png)

1. Selezionare **Rimuovi** per rimuovere il mapping delle chiavi.

1. Selezionare la casella di testo **premere il tasto di scelta rapida** .

1. Sulla tastiera premere una nuova combinazione di tasti o tasti per la Guida sensibile al contesto, ad esempio **ALT + F1**, selezionare **assegna** e quindi fare clic su **OK**.

Per altre informazioni sull'impostazione dei tasti di scelta rapida, vedere [identificare e personalizzare i tasti di scelta rapida](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
