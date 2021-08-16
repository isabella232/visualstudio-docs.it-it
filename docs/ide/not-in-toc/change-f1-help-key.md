---
title: Modificare il tasto F1 della Guida
description: Descrive come eseguire nuovamente il mapping o rimuovere il mapping dei tasti F1
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
robots: noindex,nofollow
manager: jmartens
ms.technology: vs-ide-general
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: b8864d282331024f76885fe779424b698b8cac75b50ec07b68cf9ef64edecd01
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412978"
---
# <a name="change-the-f1-help-key-in-visual-studio"></a>Modificare il tasto F1 della Guida in Visual Studio

Se si vuole usare il tasto F1 per una funzione diversa dal servizio guida F1 o si vuole semplicemente disabilitare la Guida usando F1, è possibile rimuovere o modificare il mapping dei tasti.

> [!IMPORTANT]
> Se si vuole disabilitare la Guida F1 a causa di problemi di prestazioni, è consigliabile modificare temporaneamente il mapping delle chiavi in modo da poter testare i miglioramenti apportati al servizio Guida F1 negli aggiornamenti di Visual Studio. Nella maggior parte degli scenari, F1 è un modo semplice per aprire pagine di riferimento per parole chiave del linguaggio e API dall'editor di codice o per aprire pagine della Guida associate a finestre o elementi dell'interfaccia utente nell'IDE. Se la si disabilita, la si disabilita per tutti gli usi dall'interno Visual Studio.

**Per disabilitare la Guida F1:**

1. In Visual Studio selezionare **Opzioni**  >  **strumenti**, quindi in **Ambiente** selezionare **Tastiera**.

1. Nella casella **di testo Mostra comandi contenenti** digitare **Help.f1** per filtrare la visualizzazione dei comandi.

   ![Disabilitare la Guida F1](../not-in-toc/media/disable-f1-help-key.png)

1. Selezionare **Rimuovi** per rimuovere il mapping delle chiavi.

1. Selezionare la casella **di testo Premere il tasto** di scelta rapida.

1. Sulla tastiera premere un nuovo tasto o una nuova combinazione di tasti per la Guida F1, ad esempio **ALT+F1,** selezionare **Assegna** e quindi **selezionare OK.**

Per altre informazioni sull'impostazione dei tasti di scelta rapida, vedere [Identificare e personalizzare i tasti di scelta rapida.](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
