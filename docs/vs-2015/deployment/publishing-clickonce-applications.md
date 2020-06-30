---
title: Pubblicazione di applicazioni ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 209aac56f4648554ce619cbe31cef19a8ab1fed7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531794"
---
# <a name="publishing-clickonce-applications"></a>Pubblicazione di applicazioni ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si pubblica un'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] per la prima volta, è possibile impostare le proprietà di pubblicazione con la pubblicazione guidata. Solo alcune delle proprietà sono disponibili nella procedura guidata; tutte le altre proprietà vengono impostate sui valori predefiniti.  
  
 Vengono apportate modifiche successive alle proprietà di pubblicazione nella pagina **Pubblica** di **Creazione progetti**.  
  
## <a name="publish-wizard"></a>Pubblicazione guidata  
 È possibile usare la pubblicazione guidata per configurare le impostazioni di base per la pubblicazione dell'applicazione. Ciò include le seguenti proprietà di pubblicazione:  
  
- Posizione cartella di pubblicazione: percorso in cui Visual Studio copierà i file (computer locale, condivisione file di rete, server FTP o sito Web)  
  
- Percorso cartella di installazione: percorso dal quale gli utenti finali eseguiranno l'installazione (condivisione file di rete, server FTP, sito Web, CD/DVD)  
  
- Disponibilità in linea o non in line: se gli utenti finali possono accedere all'applicazione con o senza una connessione di rete  
  
- Frequenza di aggiornamento: la frequenza con cui l'applicazione verifica la presenza di nuovi aggiornamenti.  
  
  Per altre informazioni, vedere [procedura: pubblicare un'applicazione ClickOnce mediante la pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Pagina Pubblica  
 La pagina **Pubblica** della **Creazione progetti** consente di configurare le proprietà relative alla distribuzione ClickOnce. Gli argomenti sono elencati nella tabella seguente.  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: specificare la posizione in cui vengono copiati i file in Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Viene descritto come impostare il percorso in cui Visual Studio inserisce i file di applicazione e i manifesti.|  
|[Procedura: specificare il percorso da cui gli utenti finali installeranno](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Viene descritto come impostare il percorso in cui gli utenti potranno scaricare e installare l'applicazione.|  
|[Procedura: specificare la modalità di installazione online o offline di ClickOnce](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Viene descritto come specificare se l'applicazione sarà disponibile online o offline.|  
|[Procedura: impostare la versione di pubblicazione ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)|Viene descritto come impostare la proprietà **Versione pubblicazione** di ClickOnce che determina se l'applicazione che si sta pubblicando verrà considerata o no come un aggiornamento.|  
|[Procedura: incrementare automaticamente la versione di pubblicazione ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Viene descritto come incrementare automaticamente il numero di revisione della **Versione pubblicazione** ogni volta che si pubblica l'applicazione.|  
  
 Per altre informazioni, vedere [pagina pubblica, Progettazione progetti](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Finestra di dialogo File applicazione  
 Questa finestra di dialogo consente di specificare come sono suddivisi in categorie i file del progetto per la pubblicazione, il download dinamico e l'aggiornamento. Contiene una griglia in cui sono elencati i file di progetto non esclusi per impostazione predefinita, o che hanno un gruppo di download.  
  
 Per escludere i file, contrassegnare i file come file di dati o prerequisiti e creare gruppi di file per l'installazione condizionale nell'interfaccia utente di Visual Studio, vedere [procedura: specificare quali file vengono pubblicati da ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). È anche possibile contrassegnare i file di dati con il file Mage.exe. Per altre informazioni, vedere [procedura: includere un file di dati in un'applicazione ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Prerequisiti (finestra di dialogo)  
 Questa finestra di dialogo consente di specificare quali componenti prerequisiti sono installati, nonché le relative modalità di installazione. Per altre informazioni, vedere [procedura: installare i prerequisiti con un'applicazione ClickOnce e la](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) [finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Finestra di dialogo Aggiornamenti applicazione  
 Questa finestra di dialogo consente di specificare in che modo l'installazione dell'applicazione deve controllare gli aggiornamenti. Per altre informazioni, vedere [procedura: gestire gli aggiornamenti per un'applicazione ClickOnce](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Finestra di dialogo Opzioni di pubblicazione  
 La finestra di dialogo Opzioni di pubblicazione consente di specificare le opzioni di distribuzione di un'applicazione.  
  
|Titolo|Descrizione|
|-|-|  
|[Procedura: modifica della lingua di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Viene descritto come specificare le impostazioni della lingua corrispondente alla versione localizzata.|  
|[Procedura: specificare il nome di un menu Start per un'applicazione ClickOnce](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Viene descritto come modificare il nome visualizzato per un'applicazione ClickOnce.|  
|[Procedura: specificare un collegamento per il supporto tecnico](../deployment/how-to-specify-a-link-for-technical-support.md)|Viene descritto come impostare la proprietà **URL di supporto** che identifica una pagina Web o una condivisione di file cui gli utenti possono accedere per ottenere informazioni sull'applicazione.|  
|[Procedura: specificare un URL di supporto per i singoli prerequisiti in una distribuzione ClickOnce](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|È stato illustrato come modificare manualmente un manifesto dell'applicazione in modo da includere singoli URL di supporto per ogni prerequisito.|  
|[Procedura: specificare una pagina di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Viene descritto come generare e pubblicare una pagina di Web predefinita (publish.htm) insieme all'applicazione|  
|[Procedura: personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Viene descritto come personalizzare la pagina Web che viene automaticamente generata e pubblicata insieme all'applicazione.|  
|[Procedura: abilitare l'avvio automatico per le installazioni di CD](../deployment/how-to-enable-autostart-for-cd-installations.md)|Viene descritto come attivare AutoStart per avviare automaticamente l'applicazione ClickOnce dopo l'inserimento del supporto.|  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: creare associazioni di file per un'applicazione ClickOnce](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Viene descritto come aggiungere il supporto delle estensioni di file a un'applicazione ClickOnce.|  
|[Procedura: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Viene illustrato come recuperare i parametri passati nell'URL usato per eseguire un'applicazione ClickOnce.|  
|[Procedura: disabilitare l'attivazione dell'URL delle applicazioni ClickOnce tramite la finestra di progettazione](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Viene descritto come forzare l'avvio dell'applicazione dal menu **Start** usando la finestra di progettazione.|  
|[Procedura: disabilitare l'attivazione dell'URL delle applicazioni ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Viene descritto come forzare l'avvio dell'applicazione dal menu **Start**.|  
|[Procedura dettagliata: download di assembly su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Viene spiegato come scaricare gli assembly dell'applicazione solo quando vengono innanzitutto usati dall'applicazione con la finestra di progettazione.|  
|[Procedura dettagliata: download di assembly su richiesta con l'API della distribuzione ClickOnce](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Viene spiegato come scaricare gli assembly dell'applicazione solo quando vengono innanzitutto usati dall'applicazione.|  
|[Procedura dettagliata: download di assembly satellite su richiesta con l'API della distribuzione ClickOnce](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Viene descritto come contrassegnare gli assembly satellite come facoltativi e scaricare solo l'assembly di cui un computer client ha bisogno per le impostazioni cultura correnti.|  
|[Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Viene illustrato come usare le utilità di.NET Framework per distribuire l'applicazione ClickOnce.|  
|[Procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce che non richiede una nuova firma e che conserva le informazioni di personalizzazione](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)|Viene illustrato come usare le utilità di.NET Framework per distribuire l'applicazione ClickOnce senza firmare nuovamente i manifesti.|  
|[Procedura: ottimizzare un'applicazione per un tipo di CPU specifico](https://msdn.microsoft.com/294a75d2-4279-4b72-8298-2bea05be907a)|Viene illustrato come pubblicare per un processore a 64 bit modificando la proprietà **CPU di destinazione** o **Piattaforma di destinazione** nel progetto.|  
|[Procedura dettagliata: abilitazione di un'applicazione ClickOnce per l'esecuzione in più versioni .NET Framework](https://msdn.microsoft.com/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Viene spiegato come abilitare l'installazione e l'esecuzione di un'applicazione ClickOnce in più versioni di .NET Framework.|  
|[Procedura dettagliata: creazione di un programma di installazione personalizzato per un'applicazione ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Viene spiegato come creare un programma di installazione personalizzato per installare un'applicazione ClickOnce.|  
|[Procedura: pubblicare un'applicazione WPF con stili di visualizzazione abilitata](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Vengono fornite istruzioni dettagliate per risolvere un errore che viene visualizzato quando si tenta di pubblicare un'applicazione WPF con gli stili visuali abilitati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Riferimenti di ClickOnce](../deployment/clickonce-reference.md)
