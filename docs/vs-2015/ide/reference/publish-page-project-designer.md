---
title: Pagina Pubblica, Progettazione progetti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 391e6c457dd09afa154c46cbc8644f028052cb32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665697"
---
# <a name="publish-page-project-designer"></a>Pagina Pubblica, Progettazione progetti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La pagina **Pubblica** della **Creazione progetti** consente di configurare le proprietà relative alla distribuzione ClickOnce.

 Per accedere alla pagina **Pubblica** , selezionare un nodo di progetto in **Esplora soluzioni**, quindi fare clic su **Proprietà** dal menu **Progetto**. In **Progettazione progetti** fare clic sulla scheda **Pubblica** .

> [!NOTE]
> Alcune delle proprietà ClickOnce descritte possono essere impostate anche nella **Pubblicazione guidata** disponibile nel menu **Compila** oppure facendo clic sul pulsante **Pubblicazione guidata** nella pagina.

## <a name="uielement-list"></a>Elenco UIElement
 **Percorso cartella di pubblicazione** Specifica il percorso in cui viene pubblicata l'applicazione. Può essere un percorso di unità (`C:\deploy\myapplication`), una condivisione file (`\\server\myapplication`), un server FTP (`ftp://ftp.microsoft.com/myapplication`) o un sito Web (`http://www.microsoft.com/myapplication`). Si noti che il testo deve essere presente nella scheda **Posizione di pubblicazione** perché il pulsante Sfoglia ( **...** ) funzioni.

 Per impostazione predefinita, il percorso di pubblicazione è `http://localhost/<projectname>/` se IIS è installato o la directory `publish\` se IIS non è installato. Se il computer esegue Windows Vista, il valore predefinito è sempre la directory `publish\` , indipendentemente dal fatto che sia installato IIS.

 **URL cartella di installazione** Opzionale. Specifica un sito Web a cui gli utenti accedono per installare l'applicazione. Questa operazione è necessaria solo se si tratta di un percorso diverso da **Posizione di pubblicazione**, ad esempio quando l'applicazione viene pubblicata in un server di gestione temporanea.

 **Modalità di installazione e impostazioni** Determina se l'applicazione viene eseguita direttamente dal **percorso di pubblicazione** (quando è selezionata **l'opzione applicazione disponibile solo online** ) o viene installata e aggiunta al menu **Start** e all'elemento **installazione** applicazioni in **Pannello di controllo** (quando è selezionata **l'opzione applicazione disponibile anche offline** ).

 Per le applicazioni Web Browser WPF, l'opzione **Applicazione disponibile anche offline** è disabilitata, perché tali applicazioni sono disponibili solo online.

 **File dell'applicazione** Apre la finestra di [dialogo file applicazione](https://msdn.microsoft.com/b06dff3a-b87a-4caf-996b-7a4acf8137a8), che consente di specificare come e dove vengono installati i singoli file.

 **Prerequisiti** Apre la finestra di [dialogo Prerequisiti](../../ide/reference/prerequisites-dialog-box.md), che consente di specificare i componenti dei prerequisiti, ad esempio la .NET Framework, da installare insieme all'applicazione.

 **Aggiornamenti** di Apre la finestra di [dialogo Aggiornamenti applicazione](https://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), che consente di specificare il comportamento di aggiornamento per l'applicazione. Non è disponibile quando è selezionata l'opzione **Applicazione disponibile solo online** .

 **Opzioni** di Apre la finestra di [dialogo Opzioni di pubblicazione](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), che consente di specificare opzioni di pubblicazione avanzate aggiuntive.

 **Versione di pubblicazione** Imposta il numero di versione di pubblicazione per l'applicazione. Quando il numero di versione viene modificato, l'applicazione viene pubblicata come aggiornamento. Ogni parte della versione di pubblicazione (**Principale**, **Secondaria**, **Compilazione**, **Revisione**) può avere un valore massimo di 65355 (<xref:System.UInt16.MaxValue>), il massimo consentito da <xref:System.Version>.

 Quando si installa più di una versione di un'applicazione tramite ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata Archivio, nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.

 **Incrementa automaticamente revisione a ogni pubblicazione** Opzionale. Quando questa opzione è selezionata (impostazione predefinita), la parte **Revisione** del numero di versione viene incrementata di un'unità ogni volta che viene pubblicata l'applicazione. In questo modo l'applicazione viene pubblicata come aggiornamento.

 **Pubblicazione guidata** Apre la [pubblicazione guidata](https://msdn.microsoft.com/fc6abebd-13d6-48e4-a567-fbc52dad0872). Il completamento della Pubblicazione guidata ha lo stesso effetto dell'esecuzione del comando **Pubblica** del menu **Compila** .

 **Pubblica ora** Pubblica l'applicazione usando le impostazioni correnti. Equivale al pulsante **Fine** della **Pubblicazione guidata**.

## <a name="see-also"></a>Vedere anche
 [Pubblicazione di applicazioni ClickOnce](../../deployment/publishing-clickonce-applications.md) [procedura: pubblicare un'applicazione ClickOnce usando la procedura guidata di pubblicazione](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) procedura: specificare il percorso in cui [Visual Studio copia i file](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md) [procedura: specificare il percorso in cui gli utenti finali installeranno da](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md) [come a: specificare un collegamento per il supporto tecnico](../../deployment/how-to-specify-a-link-for-technical-support.md) [procedura: specificare la modalità di installazione online o offline di ClickOnce](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md) [procedura: abilitare l'avvio automatico per le installazioni di CD](../../deployment/how-to-enable-autostart-for-cd-installations.md) [procedura: impostare la versione di pubblicazione ClickOnce](../../deployment/how-to-set-the-clickonce-publish-version.md) [procedura: incrementare automaticamente la versione di pubblicazione ClickOnce](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md) [procedura: specificare i file pubblicati da ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md) [procedura: installare i prerequisiti con un'applicazione ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) procedura [: gestire gli aggiornamenti per un'applicazione ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md) [procedura: modificare Lingua di pubblicazione per un'applicazione ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md) [procedura: specificare un nome di menu di avvio per un'applicazione ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md) [procedura: specificare una pagina di pubblicazione per un'applicazione ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md) [sicurezza e distribuzione ClickOnce](../../deployment/clickonce-security-and-deployment.md)
