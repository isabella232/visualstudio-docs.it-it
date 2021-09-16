---
title: Ripristinare Visual Studio
titleSuffix: ''
description: Informazioni su come riparare un'installazione di Visual Studio 2017
ms.date: 09/14/2021
ms.custom: vs-acquisition
ms.topic: how-to
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ca36dbefec8ff61a8ba05286f2dd8aa6593cc13b
ms.sourcegitcommit: 811e4ee80311433fefbe6d6223bf72c431008403
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2021
ms.locfileid: "127890558"
---
# <a name="repair-visual-studio"></a>Ripristinare Visual Studio

In alcuni casi l'installazione di Visual Studio può risultare danneggiata Un ripristino è utile per risolvere un'ampia gamma di problemi in fase di installazione, inclusi i problemi di aggiornamento.

## <a name="when-to-use-repair"></a>Quando usare il ripristino

Usare il ripristino se si verificano problemi con:

* Payload di installazione, che può verificarsi quando la scrittura di un file su disco ha esito negativo e il file viene danneggiato. Il ripristino può riacquisire i file necessari.
* Download sul lato client, presupponendo che siano stati risolti problemi di connessione Internet o proxy.
* Aggiornamento Visual Studio. La correzione corregge molti problemi comuni relativi all'aggiornamento.

> [!TIP] 
> Una connessione Internet instabile o un problema in un servizio Windows, ad esempio Windows Installer, può causare problemi di installazione. In questi scenari può essere interessato anche il ripristino. Per verificare la presenza di problemi sottostanti, esaminare la segnalazione errori generata dal Programma di installazione di Visual Studio.

> [!NOTE] 
> Il ripristino Visual Studio reimposta le impostazioni utente e reinstalla gli assembly esistenti. Se si verifica un problema del prodotto e il ripristino non lo risolve, creare un ticket Visual Studio [feedback.](https://aka.ms/feedback/suggest?space=8) Per altre informazioni, vedere [Come segnalare un problema](../ide/how-to-report-a-problem-with-visual-studio.md)con Visual Studio o Programma di installazione di Visual Studio .

## <a name="how-to-repair"></a>Come eseguire il ripristino
::: moniker range="vs-2017"

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

     Ad esempio, in un computer che esegue l'Aggiornamento dell'anniversario di Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

   > [!NOTE]
   > In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.
   >
   > In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Aprire il programma di installazione, scegliere **Altro** e quindi scegliere **Ripristina**.

    ![Screenshot che mostra l'opzione Ripristina nel menu a discesa Altro del Programma di installazione di Visual Studio.](media/repair-visual-studio.png "Ripristinare Visual Studio dalla Programma di installazione di Visual Studio")

   > [!NOTE]
   > Con il ripristino di Visual Studio verrà reimpostato l'ambiente. Le personalizzazioni locali verranno rimosse, ad esempio le estensioni per utente installate senza l'elevazione dei privilegi, le impostazioni utente e i profili. Verranno ripristinate le impostazioni sincronizzate, ad esempio temi, colori e tasti di scelta rapida.
   >

   > [!TIP]
   > L'opzione **Ripristina** viene visualizzata solo per le istanze installate di Visual Studio. Se non viene visualizzata l'opzione **Ripristina**, è probabile che sia stata selezionata l'opzione **Altro** in una versione inclusa nel programma di installazione di Visual Studio come "Disponibile" anziché "Installata".

::: moniker-end

::: moniker range="vs-2019"

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

     Dal menu Start in Windows è possibile cercare "programma di installazione".

     ![Screenshot che mostra il risultato di una menu Start ricerca del Programma di installazione di Visual Studio.](media/vs-2019/visual-studio-installer.png "Cercare il Programma di installazione di Visual Studio")

     > [!NOTE]
     > È anche possibile trovare il programma di installazione di Visual Studio nella posizione seguente:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata. Scegliere quindi **Altro** e **Ripristina**.

     ![Screenshot che mostra l'opzione Ripristina nel menu a discesa Altro del Programma di installazione di Visual Studio.](media/vs-2019/vs-installer-repair.png "Ripristino Visual Studio 2019")

   > [!NOTE]
   > Il ripristino Visual Studio reimposta l'ambiente. Le personalizzazioni locali verranno rimosse, ad esempio le estensioni per utente installate senza l'elevazione dei privilegi, le impostazioni utente e i profili. Verranno ripristinate le impostazioni sincronizzate, ad esempio temi, colori e tasti di scelta.
   >

   > [!TIP]
   > L'opzione **Ripristina** viene visualizzata solo per le istanze installate di Visual Studio. Se non viene visualizzata l'opzione **Ripristina**, è probabile che sia stata selezionata l'opzione **Altro** in una versione inclusa nel programma di installazione di Visual Studio come "Disponibile" anziché "Installata".

::: moniker-end

::: moniker range=">=vs-2022"

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

     Nell'menu Start in Windows cercare "installer" e quindi **selezionare** Programma di installazione di Visual Studio nei risultati.

     ![Screenshot che mostra il risultato di una menu Start ricerca del Programma di installazione di Visual Studio.](media/vs-2022/vs-installer-search.png "Cercare il Programma di installazione di Visual Studio")

     > [!NOTE]
     > È anche possibile trovare il programma di installazione di Visual Studio nella posizione seguente:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Potrebbe essere richiesto di aggiornare il Programma di installazione di Visual Studio prima di continuare. In questo caso, seguire i prompt.

1. Nel Programma di installazione di Visual Studio cercare l'installazione Visual Studio che si vuole ripristinare. Scegliere quindi **Ripristina dal** menu **a discesa** Altro.

     ![Screenshot che mostra l'opzione Ripristina nel menu a discesa Altro del Programma di installazione di Visual Studio.](media/vs-2022/vs-installer-repair.png "Ripristino Visual Studio 2022")

   > [!NOTE]
   > Il ripristino Visual Studio reimposta l'ambiente. Le personalizzazioni locali, ad esempio le estensioni per utente installate senza elevazione dei privilegi, le impostazioni utente e i profili verranno rimossi. Verranno ripristinate le impostazioni sincronizzate, ad esempio temi, colori e tasti di scelta.
   >

   > [!TIP]
   > **L'opzione** Ripristina si applica alle istanze installate di Visual Studio. Se l'opzione Ripristina non viene visualizzata nel menu a discesa  Altro, è  probabile che si sia nella scheda Disponibile anziché nella scheda Installato del Programma di installazione di Visual Studio.  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installa Visual Studio](install-visual-studio.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
* [Risoluzione dei problemi di installazione e aggiornamento di Visual Studio](troubleshooting-installation-issues.md)
