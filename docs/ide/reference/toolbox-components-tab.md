---
title: Casella degli strumenti, Scheda Componenti
description: Informazioni sui componenti disponibili nella scheda Componenti della finestra Casella degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.FrameworkComponents
- VS.CHOOSEITEMS.COMComponents
- VS.CHOOSEITEMS.UniversalWindowsComponents
helpviewer_keywords:
- Toolbox, Components tab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6925baa2d396d2b01839cdd9af083eb20867b191
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123762"
---
# <a name="toolbox-components-tab"></a>Casella degli strumenti, scheda Componenti

Visualizza i componenti che è possibile aggiungere alle finestre di progettazione di Visual Basic e C# per Windows Form. Oltre ai componenti .NET inclusi in Visual Studio, ad esempio i componenti <xref:System.Messaging.MessageQueue> e <xref:System.Diagnostics.EventLog>, in questa scheda è possibile aggiungere componenti personalizzati o di terze parti.

Per visualizzare la scheda, aprire una finestra di progettazione di Windows Form. Selezionare **Visualizza casella degli**  >  **strumenti**. In **Casella degli strumenti** selezionare la scheda **Componenti**.

## <a name="components"></a>Componenti

**BackgroundWorker**

Crea un'istanza del componente <xref:System.ComponentModel.BackgroundWorker> che può eseguire un'operazione su un thread separato dedicato. Per altre informazioni, vedere [Componente BackgroundWorker](/dotnet/framework/winforms/controls/backgroundworker-component).

**DirectoryEntry**

Crea un'istanza del componente <xref:System.DirectoryServices.DirectoryEntry> che incapsula un nodo o un oggetto nella gerarchia di Active Directory e può essere usata per interagire con i provider del servizio Active Directory.

**DirectorySearcher**

Crea un'istanza del componente <xref:System.DirectoryServices.DirectorySearcher> che è possibile usare per eseguire query in Active Directory.

**ErrorProvider**

Crea un'istanza del componente <xref:System.Windows.Forms.ErrorProvider> che indica all'utente finale che a un controllo in un form è associato un errore. Per altre informazioni, vedere [Componente ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

**EventLog**

Crea un'istanza del componente <xref:System.Diagnostics.EventLog> che consente di interagire con i log di sistema e i log eventi personalizzati, ad esempio scrivendo eventi e leggendo dati.

**FileSystemWatcher**

Crea un'istanza del componente <xref:System.IO.FileSystemWatcher> che consente di monitorare le modifiche apportate a una directory o a un file a cui si ha accesso.

**HelpProvider**

Crea un'istanza del componente <xref:System.Windows.Forms.HelpProvider> che offre informazioni della Guida, anche in finestre popup. Per altre informazioni, vedere [Componente HelpProvider](/dotnet/framework/winforms/controls/helpprovider-component-windows-forms).

**Imagelist**

Crea un'istanza del componente <xref:System.Windows.Forms.ImageList> che rende disponibili metodi per la gestione di una raccolta di oggetti <xref:System.Drawing.Image>. Per altre informazioni, vedere [Componente ImageList](/dotnet/framework/winforms/controls/imagelist-component-windows-forms).

**MessageQueue**

Crea un'istanza del componente <xref:System.Messaging.MessageQueue> che consente di interagire con le code di messaggi, leggendo e scrivendo messaggi nelle code, elaborando transazioni ed eseguendo attività di amministrazione delle code.

**Performancecounter**

Crea un'istanza del componente <xref:System.Diagnostics.PerformanceCounter> che consente di interagire con i contatori delle prestazioni di Windows, creando nuove categorie e istanze, leggendo valori dai contatori ed eseguendo calcoli sui dati dei contatori stessi.

**Processo**

Crea un'istanza del componente <xref:System.Diagnostics.Process> che consente di arrestare e avviare i processi del sistema, nonché di manipolare i dati associati a questi.

**SerialPort**

Crea un'istanza del componente <xref:System.IO.Ports.SerialPort> che rende disponibili le funzioni di I/O sincrono e basato su eventi, l'accesso agli stati di blocco e interruzione, l'accesso alle proprietà del driver seriale.

**ServiceController**

Crea un'istanza del componente <xref:System.ServiceProcess.ServiceController> che consente di manipolare i servizi esistenti, avviandoli e arrestandoli e inviando loro dei comandi.

**Timer**

Crea un'istanza del componente <xref:System.Windows.Forms.Timer> che consente di aggiungere funzionalità basate sull'ora alle applicazioni basate su Windows. Per altre informazioni, vedere [Componente Timer](/dotnet/framework/winforms/controls/timer-component-windows-forms).

> [!NOTE]
> È disponibile anche un componente <xref:System.Timers.Timer> basato su sistema che è possibile aggiungere alla **Casella degli strumenti**. Il componente <xref:System.Timers.Timer> è ottimizzato per le applicazioni server mentre il componente <xref:System.Windows.Forms.Timer> di Windows Forms è più adatto all'uso con Windows Forms.

## <a name="see-also"></a>Vedi anche

- [Controlli da usare in Windows form](/dotnet/framework/winforms/controls/controls-to-use-on-windows-forms)
- [Scegli elementi della Casella degli strumenti, Componenti WPF](choose-toolbox-items-wpf-components.md)
- [Casella degli strumenti](../../ide/reference/toolbox.md)
