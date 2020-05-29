---
title: Disinstallare Visual Studio
titleSuffix: ''
description: Informazioni sulla procedura di disinstallazione di Visual Studio.
ms.date: 05/06/2020
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
ms.openlocfilehash: 6b5377c9bdb83c5c67816b3567656c49cf707071
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184419"
---
# <a name="uninstall-visual-studio"></a>Disinstallare Visual Studio

In questa pagina viene descritta la procedura di disinstallazione di Visual Studio, la suite integrata di strumenti di produttività per gli sviluppatori.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Disinstallare Visual Studio per Mac](/visualstudio/mac/uninstall).

> [!TIP]
> Se si verificano problemi con l'istanza di Visual Studio, provare lo strumento di **ripristino** . Per altre informazioni, vedere [Repair Visual Studio](../install/repair-visual-studio.md). 
>
> Se si vuole modificare il percorso di alcuni file di Visual Studio, è possibile farlo senza disinstallare l'istanza corrente. Per altre informazioni, vedere [selezionare i percorsi di installazione in Visual Studio](../install/change-installation-locations.md).
>
> Per suggerimenti generali per la risoluzione dei problemi, vedere [risolvere i problemi di installazione e aggiornamento di Visual Studio](../install/troubleshooting-installation-issues.md).

::: moniker range="vs-2017"

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue l'Aggiornamento dell'anniversario di Windows 10 selezionare **Start** e scorrere fino alla lettera **P**, in cui è elencato come **Programma di installazione di Visual Studio**.

     ![Programma di installazione di Visual Studio](media/locate-the-visual-studio-installer.png "Individuare il programma di installazione Microsoft Visual Studio")

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

     ![Aprire il Programma di installazione di Visual Studio](media/vs-2019/vs-installer-windows-start.png "Aprire il Programma di installazione di Visual Studio")

     > [!NOTE]
     > È anche possibile trovare il programma di installazione di Visual Studio nella posizione seguente:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata. Scegliere quindi **Altro** e **Disinstalla**.

     ![Disinstallare Visual Studio 2019](media/vs-2019/vs-installer-uninstall.png "Disinstallare Visual Studio 2019")

1. Fare clic su **OK** per confermare la scelta.

     ![Disinstalla conferma di Visual Studio](media/vs-2019/uninstall-visualstudio-confirm.png "Confermare che si vuole disinstallare Visual Studio 2019")

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

Se si verifica un errore irreversibile e non è possibile disinstallare Visual Studio usando le istruzioni precedenti, è possibile usare invece l'opzione "ultima risorsa". Per ulteriori informazioni su come rimuovere completamente tutti i file di installazione di Visual Studio e tutte le informazioni sul prodotto, vedere la pagina [rimuovere Visual Studio](remove-visual-studio.md) .

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Modificare Visual Studio](modify-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
