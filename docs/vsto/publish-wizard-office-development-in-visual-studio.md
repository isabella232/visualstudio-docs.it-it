---
title: Pubblicazione guidata (sviluppo per Office in Visual Studio)
description: Informazioni su come utilizzare la pubblicazione guidata per copiare i file di soluzione in un percorso specificato, creare i file manifesto e creare un programma di installazione in Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 25821a0f245f2f0ed30fcbfb10137a772dd0dd01
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528020"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Pubblicazione guidata (sviluppo per Office in Visual Studio)
  Usare la **pubblicazione guidata** per copiare i file di soluzione in un percorso specificato, creare i file manifesto e creare un programma di installazione.

 Per accedere a questa procedura guidata, scegliere **pubblica** *soluzione* dal menu **Compila** . È inoltre possibile accedere alla **pubblicazione guidata** da **Esplora soluzioni**. Aprire il menu di scelta rapida per il nodo del progetto, quindi scegliere **pubblica**.

 Ogni sezione seguente descrive una pagina della procedura guidata.

## <a name="where-do-you-want-to-publish-the-application"></a>Scegliere la posizione in cui pubblicare l'applicazione.
 **Specificare il percorso in cui pubblicare l'applicazione** Obbligatorio. Il percorso di pubblicazione è la directory in cui la **pubblicazione guidata** copia i file della soluzione, ad esempio manifesti, assembly, certificati temporanei e altri file dalla compilazione. È necessario l'accesso in scrittura a questa directory.

 Digitare il percorso come percorso del disco, condivisione file, sito FTP o URL del sito Web oppure fare clic sul pulsante **Sfoglia** per cercare il percorso. Il percorso può essere in questi formati:

- Percorso relativo o assoluto in formato Windows standard, ad esempio *c:\distribuzione\applicazione* o *\applicazione*.

- Un percorso di Universal Naming Convention (UNC), ad esempio *\\ \ServerName\MyApplication \\*.

- URL di un sito Web, ad esempio `http://www.contoso.com/MyApplication` .

  Per impostazione predefinita, il percorso di pubblicazione è *http://localhost/projectname/* se IIS è installato o la directory publish \ se IIS non è installato.

> [!NOTE]
> Se nel computer di destinazione è in esecuzione Windows Vista, sono presenti ulteriori considerazioni. Per utilizzare l'opzione di pubblicazione locale, è necessario essere un amministratore del computer con Windows Vista. Inoltre, il percorso predefinito è sempre la directory *di \\ pubblicazione* , indipendentemente dal fatto che sia installato IIS.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Qual è il percorso di installazione predefinito nei computer degli utenti finali?
 Il percorso di installazione è facoltativo. Se si preferisce, è possibile impostare il percorso di installazione in un secondo momento. Per informazioni dettagliate, vedere [procedura: modificare il percorso di installazione di una soluzione Office](/previous-versions/bb608626(v=vs.110)).

 Il percorso di installazione è la directory da cui l'utente finale installerà la personalizzazione. È anche il percorso usato dalla soluzione per controllare la disponibilità di aggiornamenti. La **pubblicazione guidata** non distribuisce la soluzione in questo percorso, a meno che il percorso non corrisponda a quello immesso nella casella **specificare il percorso di pubblicazione dell'applicazione** nella pagina precedente.

 **Da un sito Web** Specificare l'URL che gli utenti finali seguiranno per installare la soluzione.

 **Da un percorso UNC o da una condivisione file** Specificare il percorso UNC che gli utenti finali seguiranno per installare la soluzione.

 **Da CD-ROM o DVD-ROM** Questa opzione non richiede un percorso di installazione.

 Visual Studio non Masterizza il CD o il DVD. È necessario copiare manualmente l'output in un CD o DVD.

## <a name="see-also"></a>Vedere anche
- [Distribuire una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Pagina pubblica, Progettazione progetti &#40;sviluppo per Office in Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)