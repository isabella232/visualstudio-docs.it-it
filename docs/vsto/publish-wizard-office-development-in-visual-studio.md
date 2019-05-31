---
title: Pubblicazione guidata (sviluppo per Office in Visual Studio)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7879ad7cf18c3d09fddbab3923296e0896688af9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447064"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Pubblicazione guidata (sviluppo per Office in Visual Studio)
  Usare la **pubblicazione guidata** per copiare i file della soluzione in una posizione specificata, creare i file manifesto e creare un programma di installazione.

 Per accedere a questa procedura guidata, scegliere il **compilare** menu, scegliere **Publish** *SolutionName*. È possibile accedere anche il **pubblicazione guidata** dalla **Esplora soluzioni**. Aprire il menu di scelta rapida per il nodo del progetto e quindi scegliere **pubblica**.

 Ogni sezione seguente descrive una pagina della procedura guidata.

## <a name="where-do-you-want-to-publish-the-application"></a>In cui si desidera pubblicare l'applicazione?
 **Specificare il percorso per pubblicare l'applicazione** necessari. Percorso di pubblicazione è la directory in cui il **pubblicazione guidata** copia i file della soluzione, ad esempio i manifesti, gli assembly, il certificato temporaneo e altri file dalla compilazione. È necessario l'accesso in scrittura a questa directory.

 Digitare il percorso come un percorso su disco, una condivisione file, un sito FTP o URL del sito web o il **esplorare** per cercare il percorso. Il percorso può essere nei seguenti formati:

- Percorso relativo o assoluto nello standard Windows formato, ad esempio *C:\Deploy\MyApplication* oppure *\MyApplication*.

- Un percorso Universal Naming Convention (UNC), ad esempio  *\\\ServerName\MyApplication\\* .

- Un URL di un sito web del sito, ad esempio http://www.microsoft.com/MyApplication.

  Per impostazione predefinita, è il percorso di pubblicazione *http://localhost/projectname/* se è installato IIS o la directory Publish \ se IIS non è installato.

> [!NOTE]
> Se il computer di destinazione è in esecuzione Windows Vista, esistono ulteriori considerazioni. È necessario essere un amministratore nel computer Windows Vista per utilizzare l'opzione di pubblicazione locale. Inoltre, il percorso predefinito è sempre il *pubblicare\\*  directory, indipendentemente dal fatto che è installato IIS.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Che cos'è il percorso di installazione predefinito sul computer degli utenti finali?
 Il percorso di installazione è facoltativo. Se si preferisce, è possibile impostare il percorso di installazione in un secondo momento. Per informazioni dettagliate, vedere [Procedura: Modificare il percorso di installazione di una soluzione Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 Il percorso di installazione è la directory da cui l'utente finale installerà la personalizzazione. È anche il percorso usato dalla soluzione per controllare la disponibilità di aggiornamenti. Il **pubblicazione guidata** distribuisce la soluzione in questa posizione, a meno che il percorso è identico a quello immesso nella **specificare il percorso per pubblicare l'applicazione** casella sulla pagina precedente.

 **Da un sito Web** specificare l'URL che gli utenti finali deve seguire per installare la soluzione.

 **Da una condivisione di file o percorso UNC** specificare il percorso UNC che gli utenti finali deve seguire per installare la soluzione.

 **Da un CD-ROM o DVD-ROM** questa opzione non richiede un percorso di installazione.

 Visual Studio non masterizzare il CD o DVD. È necessario copiare manualmente l'output su un CD o DVD.

## <a name="see-also"></a>Vedere anche
- [Distribuire una soluzione Office usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Pagina pubblica, creazione progetti &#40;sviluppo per Office in Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
