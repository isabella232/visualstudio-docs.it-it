---
title: Pubblicazione guidata (Office sviluppo in Visual Studio)
description: Informazioni su come usare la Pubblicazione guidata per copiare i file della soluzione in un percorso specificato, creare i file manifesto e creare un programma di installazione in Visual Studio.
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 5078179f4dbe0ba65ada1ec0dee6e3aeeefbc094
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099542"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Pubblicazione guidata (Office sviluppo in Visual Studio)
  Usare la **Pubblicazione guidata per** copiare i file della soluzione in un percorso specificato, creare i file manifesto e creare un programma di installazione.

 Per accedere a questa procedura guidata, **scegliere** **Pubblica** Nome Soluzione dal menu *Compila*. È anche possibile accedere alla **Pubblicazione guidata** da **Esplora soluzioni**. Aprire il menu di scelta rapida per il nodo del progetto e quindi scegliere **Pubblica**.

 Ogni sezione seguente descrive una pagina della procedura guidata.

## <a name="where-do-you-want-to-publish-the-application"></a>Dove si vuole pubblicare l'applicazione?
 **Specificare il percorso in cui pubblicare l'applicazione** Obbligatorio. Il percorso di pubblicazione  è la directory in cui la Pubblicazione guidata copia i file della soluzione, ad esempio manifesti, assembly, certificato temporaneo e altri file dalla compilazione. È necessario l'accesso in scrittura a questa directory.

 Digitare il percorso come percorso del disco, condivisione file, sito  FTP o URL del sito Web oppure fare clic sul pulsante Sfoglia per cercare il percorso. Il percorso può essere nei formati seguenti:

- Percorso relativo o assoluto in formato Windows standard, ad esempio *C:\Deploy\MyApplication* o *\MyApplication*.

- Un Universal Naming Convention (UNC), ad esempio *\\ \ServerName\MyApplication \\*.

- URL di un sito Web, ad esempio `http://www.contoso.com/MyApplication` .

  Per impostazione predefinita, il percorso di pubblicazione è se è installato IIS o la directory publish\ se *http://localhost/projectname/* IIS non è installato.

> [!NOTE]
> Esistono altre considerazioni se il computer di destinazione esegue Windows Vista. È necessario essere un amministratore nel computer Windows Vista per usare l'opzione di pubblicazione locale. Inoltre, il percorso predefinito è sempre la directory *di \\* pubblicazione, indipendentemente dal fatto che IIS sia installato.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Qual è il percorso di installazione predefinito nei computer degli utenti finali?
 Il percorso di installazione è facoltativo. Se si preferisce, è possibile impostare il percorso di installazione in un secondo momento. Per informazioni dettagliate, [vedere Procedura: Modificare il percorso di installazione](/previous-versions/bb608626(v=vs.110))di una Office soluzione .

 Il percorso di installazione è la directory da cui l'utente finale installerà la personalizzazione. È anche il percorso usato dalla soluzione per controllare la disponibilità di aggiornamenti. La **Pubblicazione guidata** non distribuisce la soluzione in questo percorso, a meno  che il percorso non sia uguale a quello immesso nella casella Specificare il percorso in cui pubblicare l'applicazione nella pagina precedente.

 **Da un sito Web** Specificare l'URL che gli utenti finali seguiranno per installare la soluzione.

 **Da un percorso UNC o da una condivisione file** Specificare il percorso UNC che gli utenti finali seguiranno per installare la soluzione.

 **Da un CD-ROM o DVD-ROM** Questa opzione non richiede un percorso di installazione.

 Visual Studio masterizza il CD o il DVD. È necessario copiare manualmente l'output in un CD o DVD.

## <a name="see-also"></a>Vedi anche
- [Distribuire una Office di distribuzione usando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Pagina Pubblica, Project Designer &#40;Office sviluppo in Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)