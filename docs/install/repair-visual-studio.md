---
title: Ripristinare Visual Studio
titleSuffix: ''
description: Informazioni su come riparare un'installazione di Visual Studio 2017
ms.date: 06/15/2020
ms.custom: seodec18
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fda72206059e5c14c46d332e44ea0de481004296
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85418964"
---
# <a name="repair-visual-studio"></a>Ripristinare Visual Studio

In alcuni casi l'installazione di Visual Studio può risultare danneggiata Una correzione è utile per la correzione di problemi in fase di installazione per tutte le operazioni di installazione, inclusi gli aggiornamenti.

## <a name="when-to-use-repair"></a>Quando usare Repair
* Se si verificano problemi di payload di installazione. Questo problema può verificarsi quando la scrittura del file su disco ha esito negativo e non può essere risolto eliminando il file danneggiato. Il ripristino può acquisire nuovamente i file necessari. 
* Se si verificano problemi di download sul lato client. Supponendo che siano stati risolti eventuali problemi di connessione o proxy, il ripristino potrebbe essere utile. 
* Se si verificano problemi durante l'aggiornamento di Visual Studio. Riparazione corregge molti problemi di aggiornamento comuni. 

> [!TIP] 
> Se il problema di installazione è causato da un problema in un servizio di Windows sottostante, ad esempio Windows Installer, la correzione può raggiungere lo stesso problema. I problemi sistemici possono includere una connessione Internet Windows Installer o instabile. Per verificare la presenza di un problema di sistemi, utilizzare il report di errore generato dall'operazione di installazione.

> [!NOTE] 
> Il ripristino di Visual Studio Reimposta le impostazioni utente e installa di nuovo gli assembly già presenti. Se si verifica un problema del prodotto, creare un [ticket di feedback di Visual Studio](https://developercommunity.visualstudio.com/content/problem/post.html?space=8), in quanto il ripristino potrebbe non risolvere il problema.

## <a name="how-to-repair"></a>Come ripristinare
::: moniker range="vs-2017"

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

     Ad esempio, in un computer che esegue l'Aggiornamento dell'anniversario di Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

   > [!NOTE]
   > In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.
   >
   > In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Aprire il programma di installazione, scegliere **Altro** e quindi scegliere **Ripristina**.

    ![Ripristinare Visual Studio dalla Programma di installazione di Visual Studio](media/repair-visual-studio.png "Ripristinare Visual Studio dalla Programma di installazione di Visual Studio")

   > [!NOTE]
   > Con il ripristino di Visual Studio verrà reimpostato l'ambiente. Le personalizzazioni locali verranno rimosse, ad esempio le estensioni per utente installate senza l'elevazione dei privilegi, le impostazioni utente e i profili. Verranno ripristinate le impostazioni sincronizzate, ad esempio temi, colori e tasti di scelta rapida.
   >

   > [!TIP]
   > L'opzione **Ripristina** viene visualizzata solo per le istanze installate di Visual Studio. Se non viene visualizzata l'opzione **Ripristina**, è probabile che sia stata selezionata l'opzione **Altro** in una versione inclusa nel programma di installazione di Visual Studio come "Disponibile" anziché "Installata".

::: moniker-end

::: moniker range="vs-2019"

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

     Ad esempio, in un computer che esegue Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

     ![Aprire il Programma di installazione di Visual Studio](media/vs-2019/vs-installer-windows-start.png "Aprire il Programma di installazione di Visual Studio")

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

* [Installa Visual Studio](install-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
* [Risoluzione dei problemi di installazione e aggiornamento di Visual Studio](troubleshooting-installation-issues.md)
