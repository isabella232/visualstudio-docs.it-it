---
title: Ripristinare Visual Studio
titleSuffix: ''
description: Informazioni su come riparare un'installazione di Visual Studio 2017
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 3ba5cdf7ba627bc1d6a75368d90da5ce8a726a5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973215"
---
# <a name="repair-visual-studio"></a>Ripristinare Visual Studio

::: moniker range="vs-2017"

In alcuni casi l'installazione di Visual Studio può risultare danneggiata ed è possibile ripararla per risolvere il problema.

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

     Ad esempio, in un computer che esegue l'Aggiornamento dell'anniversario di Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

   > [!NOTE]
   > In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.
   >
   > In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Aprire il programma di installazione, scegliere **Altro** e quindi scegliere **Ripristina**.

    ![Ripristinare Visual Studio dal programma di installazione di Visual Studio](media/repair-visual-studio.png "Ripristinare Visual Studio dal programma di installazione di Visual Studio")
    
   > [!NOTE]
   > Con il ripristino di Visual Studio verrà reimpostato l'ambiente. Le personalizzazioni locali verranno rimosse, ad esempio le estensioni per utente installate senza l'elevazione dei privilegi, le impostazioni utente e i profili. Verranno ripristinate le impostazioni sincronizzate, ad esempio temi, colori e tasti di scelta rapida.
   >

   > [!TIP]
   > L'opzione **Ripristina** viene visualizzata solo per le istanze installate di Visual Studio. Se non viene visualizzata l'opzione **Ripristina**, è probabile che sia stata selezionata l'opzione **Altro** in una versione inclusa nel programma di installazione di Visual Studio come "Disponibile" anziché "Installata".

::: moniker-end

::: moniker range="vs-2019"

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

     ![Aprire il programma di installazione di Visual Studio](media/vs2019-visual-studio-installer.png "Aprire il programma di installazione di Visual Studio")

     > [!NOTE]
     > È anche possibile trovare il programma di installazione di Visual Studio nella posizione seguente:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata. Scegliere quindi **Altro** e **Ripristina**.

     ![Ripristinare Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Ripristinare Visual Studio 2019")

   > [!NOTE]
   > Con il ripristino di Visual Studio verrà reimpostato l'ambiente. Le personalizzazioni locali verranno rimosse, ad esempio le estensioni per utente installate senza l'elevazione dei privilegi, le impostazioni utente e i profili. Verranno ripristinate le impostazioni sincronizzate, ad esempio temi, colori e tasti di scelta rapida.
   >

   > [!TIP]
   > L'opzione **Ripristina** viene visualizzata solo per le istanze installate di Visual Studio. Se non viene visualizzata l'opzione **Ripristina**, è probabile che sia stata selezionata l'opzione **Altro** in una versione inclusa nel programma di installazione di Visual Studio come "Disponibile" anziché "Installata".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio](install-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
* [Risoluzione dei problemi di installazione e aggiornamento di Visual Studio](troubleshooting-installation-issues.md)
