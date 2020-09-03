---
title: Casella degli strumenti, Scheda Componenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Components tab
ms.assetid: 332fafab-a763-4244-b388-15d1b5b5cc04
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce18767d95b3ac539737d78acbd2259dcda0a036
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661575"
---
# <a name="toolbox-components-tab"></a>Casella degli strumenti, Scheda Componenti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Consente di visualizzare i componenti che è possibile aggiungere alle finestre di progettazione di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] e [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Oltre ai [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] componenti inclusi in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , ad esempio i <xref:System.Messaging.MessageQueue> <xref:System.Diagnostics.EventLog> componenti e, è possibile aggiungere componenti personalizzati o di terze parti a questa scheda. Per altre informazioni, vedere [procedura: modificare le schede della casella degli strumenti](https://msdn.microsoft.com/21285050-cadd-455a-b1f5-a2289a89c4db).

 Per visualizzare questa scheda, scegliere **Casella degli strumenti** dal menu **Visualizza**. Nella **Casella degli strumenti** selezionare la scheda **Componenti**.

 **BackgroundWorker** Crea un' `System.ComponentModel.BackgroundWorker` istanza del componente che può eseguire un'operazione su un thread separato dedicato.

 **DirectoryEntry** Crea un' <xref:System.DirectoryServices.DirectoryEntry> istanza del componente che incapsula un nodo o un oggetto nella gerarchia di Active Directory e può essere utilizzato per interagire con Active Directory provider di servizi.

 **DirectorySearcher** Crea un' <xref:System.DirectoryServices.DirectorySearcher> istanza del componente che è possibile utilizzare per eseguire query sul Active Directory.

 **ErrorProvider** Crea un' `System.Windows.Forms.ErrorProvider` istanza del componente che indica all'utente finale che a un controllo di un form è associato un errore.

 **Registro eventi** Consente di creare un' <xref:System.Diagnostics.EventLog> istanza del componente che è possibile utilizzare per interagire con i registri eventi di sistema e personalizzati, inclusa la scrittura di eventi in un log e la lettura dei dati del log. Per altre informazioni, vedere [Introduzione al componente EventLog](https://msdn.microsoft.com/a2ba4f28-4b1a-435e-99ef-51b28e21f805).

 **FileSystemWatcher** Consente di creare un' <xref:System.IO.FileSystemWatcher> istanza del componente che è possibile utilizzare per monitorare le modifiche apportate a una directory o a un file a cui si ha accesso. Per altre informazioni, vedere [Procedura: configurare istanze del componente FileSystemWatcher](https://msdn.microsoft.com/2e628234-4951-4135-8a86-28b924070d50).

 **HelpProvider** Crea un' `System.Windows.Forms.HelpProvider` istanza del componente che fornisce la Guida popup o la Guida in linea per i controlli.

 **ImageList** Crea un' `System.Windows.Forms.ImageList` istanza del componente che fornisce i metodi per gestire una raccolta di `System.Drawing.Image` oggetti.

 **MessageQueue** Crea un' <xref:System.Messaging.MessageQueue> istanza del componente che è possibile utilizzare per interagire con le code di messaggi, inclusa la lettura di messaggi e la scrittura di messaggi nelle code, l'elaborazione delle transazioni e l'esecuzione di attività di amministrazione delle code. Per altre informazioni, vedere [Utilizzo dei componenti di messaggistica](https://msdn.microsoft.com/922dbac7-26f0-4e39-b666-ccfc184793d7).

 **PerformanceCounter** Consente di creare un' <xref:System.Diagnostics.PerformanceCounter> istanza del componente che è possibile utilizzare per interagire con i contatori delle prestazioni di Windows, tra cui la creazione di nuove categorie e istanze, la lettura di valori dai contatori e l'esecuzione di calcoli sui dati dei contatori. Per altre informazioni, vedere [Monitoraggio dei valori limite delle prestazioni](https://msdn.microsoft.com/b8b44a55-31d0-4b45-9517-8c1b1e4fdc91).

 **Processo** di Consente di creare un' <xref:System.Diagnostics.Process> istanza del componente che è possibile utilizzare per arrestare, avviare e modificare i dati associati ai processi nel sistema. Per altre informazioni, vedere [Monitoraggio e gestione di processi Windows](https://msdn.microsoft.com/a86bd4c1-b92c-49a0-8f32-61d67837b45e).

 **SerialPort** Crea un' `System.IO.Ports.SerialPort` istanza del componente che fornisce l'I/O sincrono e basato su eventi, l'accesso agli Stati di blocco e di interruzioni e l'accesso alle proprietà del driver seriale.

 **ServiceController** Consente di creare un' <xref:System.ServiceProcess.ServiceController> istanza del componente che è possibile utilizzare per modificare i servizi esistenti, inclusi l'avvio e l'arresto dei servizi e l'invio di comandi. Per altre informazioni, vedere [Monitoraggio di servizi Windows](https://msdn.microsoft.com/4542ee3f-e052-4cb9-8726-58e9420de222).

 **Timer** di Consente di creare un' <xref:System.Windows.Forms.Timer> istanza del componente che è possibile utilizzare per aggiungere funzionalità basate sul tempo alle applicazioni basate su Windows. Per altre informazioni, vedere [Componente Timer](https://msdn.microsoft.com/library/6700e534-6382-43d5-98ed-14205435fff7).

> [!NOTE]
> È disponibile anche un componente <xref:System.Timers.Timer> basato su sistema che è possibile aggiungere alla **Casella degli strumenti**. Il componente <xref:System.Timers.Timer> è ottimizzato per le applicazioni server mentre il componente <xref:System.Windows.Forms.Timer> di Windows Forms è più adatto all'uso con Windows Forms.

## <a name="see-also"></a>Vedere anche
 [Programmazione con componenti](https://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3) [componente procedure dettagliate](https://msdn.microsoft.com/library/373cacf7-479e-4b05-991c-5cb18824e913) della [casella degli strumenti](../../ide/reference/toolbox.md) [finestra di dialogo Scegli elementi della casella degli strumenti (Visual Studio)](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb)
