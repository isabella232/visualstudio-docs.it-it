---
title: Disinstallare Visual Studio
titleSuffix: ''
description: Informazioni sulla procedura di disinstallazione di Visual Studio.
ms.date: 12/19/2019
ms.custom: seodec18
ms.topic: conceptual
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fd21f01f89cb4fe4507775670968496cbb5f99f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115009"
---
# <a name="uninstall-visual-studio"></a>Disinstallare Visual Studio

In questa pagina viene descritta la procedura di disinstallazione di Visual Studio, la suite integrata di strumenti di produttività per gli sviluppatori.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Disinstallare Visual Studio per Mac](/visualstudio/mac/uninstall).

::: moniker range="vs-2017"

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue l'Aggiornamento dell'anniversario di Windows 10 selezionare **Start** e scorrere fino alla lettera **P**, in cui è elencato come **Programma di installazione di Visual Studio**.

     ![Programma di installazione di Visual Studio](media/locate-the-visual-studio-installer.png "Individuare il programma di installazione di Microsoft Visual Studio")

   > [!NOTE]
   > In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.<br/><br/> In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Nel programma di installazione cercare l'edizione di Visual Studio installata. Scegliere quindi **Altro** e **Disinstalla**.

     ![Disinstallare Visual Studio 2017](media/uninstall-visual-studio.png "Disinstallare Visual Studio 2017")

1. Fare clic su **OK** per confermare la scelta.

Se in seguito si cambia idea e si vuole reinstallare Visual Studio 2017, avviare nuovamente il programma di installazione di Visual Studio e quindi selezionare **Installa** nella schermata di selezione.

## <a name="uninstall-visual-studio-installer"></a>Disinstallazione del Programma di installazione di Visual Studio

Per rimuovere completamente dal computer tutte le installazioni di Visual Studio 2017 e il programma di installazione di Visual Studio, eseguirne la disinstallazione da App e funzionalità.

1. In Windows 10 digitare **App e funzionalità** nella casella "Digitare qui il testo di ricerca".
1. Trovare **Microsoft Visual Studio 2017** (oppure **Visual Studio 2017**).
1. Scegliere **Disinstalla**.
1. Trovare quindi il **programma di installazione di Microsoft Visual Studio**.
1. Scegliere **Disinstalla**.

::: moniker-end

::: moniker range="vs-2019"

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

     ![Aprire il programma di installazione di Visual StudioOpen the Visual Studio Installer](media/vs-2019/vs-installer-windows-start.png "Aprire il programma di installazione di Visual StudioOpen the Visual Studio Installer")

     > [!NOTE]
     > È anche possibile trovare il programma di installazione di Visual Studio nella posizione seguente:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata. Scegliere quindi **Altro** e **Disinstalla**.

     ![Disinstallare Visual Studio 2019](media/vs-2019/vs-installer-uninstall.png "Disinstallare Visual Studio 2019")

1. Fare clic su **OK** per confermare la scelta.

     ![Disinstallare la conferma di Visual Studio](media/vs-2019/uninstall-visualstudio-confirm.png "Confermare che si desidera disinstallare Visual Studio 2019")

Se in seguito si cambia idea e si vuole reinstallare Visual Studio 2019, avviare nuovamente il programma di installazione di Visual Studio, selezionare la scheda **Disponibile**, scegliere la versione di Visual Studio che si vuole installare e quindi selezionare **Installa**.

## <a name="uninstall-visual-studio-installer"></a>Disinstallazione del Programma di installazione di Visual Studio

Per rimuovere dal computer tutte le installazioni di Visual Studio 2019 e il programma di installazione di Visual Studio, eseguirne la disinstallazione da App e funzionalità.

1. In Windows 10 digitare **App e funzionalità** nella casella "Digitare qui il testo di ricerca".
1. Trovare **Visual Studio 2019**.
1. Scegliere **Disinstalla**.
1. Trovare quindi il **programma di installazione di Microsoft Visual Studio**.
1. Scegliere **Disinstalla**.

::: moniker-end

## <a name="remove-all-files"></a>Rimuovi tutti i file

Se si verifica un errore irreversibile e non è possibile disinstallare Visual Studio utilizzando le istruzioni precedenti, è disponibile un'opzione "ultima risorsa" che è possibile considerare l'utilizzo. Per altre informazioni su come rimuovere completamente tutti i file di installazione e le informazioni sul prodotto di Visual Studio, vedere la pagina [Rimuovi Visual Studio.For](remove-visual-studio.md) more information about how to remove all Visual Studio installation files and product information completely, see the Remove Visual Studio page.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Modificare Visual Studio](modify-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
