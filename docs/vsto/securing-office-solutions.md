---
title: Proteggere Office soluzioni
description: Informazioni sul modo in cui il modello di sicurezza Office soluzioni implica diverse tecnologie, tra cui il runtime Visual Studio Tools per Office e ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: abe2d548fc79788c650debde06fa1a6847026839
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633804"
---
# <a name="secure-office-solutions"></a>Proteggere Office soluzioni
  Il modello di sicurezza per le Office prevede diverse tecnologie: , , il Centro protezione di Microsoft Office e l'area Internet Explorer siti [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] con restrizioni. Le sezioni seguenti descrivono il funzionamento delle diverse funzionalità di sicurezza:

- [Concedere l'attendibilità Office soluzioni](#GrantingTrustToSolutions)

- [Concedere l'attendibilità ai documenti](#GrantingTrustToDocuments)

- [Concedere l'attendibilità quando si usa il Windows di installazione](#GrantingTrustWindowsInstaller)

- [Considerazioni specifiche sulla sicurezza per Office soluzioni](#Security)

- [Sicurezza durante lo sviluppo](#SecurityDuringDeployment)

- [Visual Studio Tools per Office Runtime](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="grant-trust-to-office-solutions"></a><a name="GrantingTrustToSolutions"></a>Concedere l'attendibilità Office soluzioni
 La concessione dell'attendibilità alle soluzioni Office prevede la modifica dei criteri di sicurezza di tutti gli utenti finali in modo che la soluzione Office venga considerata attendibile in base alla seguente evidenza:

- Il certificato usato per firmare il manifesto della distribuzione.

- L'URL del manifesto della distribuzione.

  Per altre informazioni, vedere [Concedere l'attendibilità Office soluzioni](../vsto/granting-trust-to-office-solutions.md).

## <a name="grant-trust-to-documents"></a><a name="GrantingTrustToDocuments"></a> Concedere l'attendibilità ai documenti
 Una personalizzazione a livello di documento richiede che il documento si trovi in una directory progettata come percorso attendibile. Per altre informazioni, vedere [Concedere l'attendibilità ai documenti.](../vsto/granting-trust-to-documents.md)

## <a name="grant-trust-when-using-windows-installer"></a><a name="GrantingTrustWindowsInstaller"></a>Concedere l'attendibilità quando si usa Windows installer
 È possibile usare Windows Installer per creare un file MSI per installare le soluzioni Office nella directory Programmi, che richiede diritti di amministratore. Per Office soluzioni nella directory Programmi, il runtime di Visual Studio 2010 Tools for Office considera attendibili queste soluzioni Office e non visualizza la richiesta di attendibilità ClickOnce.

## <a name="specific-security-considerations-for-office-solutions"></a><a name="Security"></a>Considerazioni specifiche sulla sicurezza per Office soluzioni
 Le funzionalità di sicurezza fornite da [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] e Microsoft Office possono contribuire alla protezione contro diverse possibili minacce alla sicurezza nelle soluzioni Office. Per altre informazioni, vedere [Considerazioni specifiche sulla sicurezza per Office soluzioni](../vsto/specific-security-considerations-for-office-solutions.md).

## <a name="security-during-development"></a><a name="SecurityDuringDeployment"></a> Sicurezza durante lo sviluppo
 Per semplificare il processo di sviluppo, Visual Studio imposta i criteri di sicurezza necessari per eseguire ed eseguire il debug della soluzione nel computer ogni volta che si compila un progetto. In alcuni scenari, è necessario aggiungere altri passaggi di sicurezza per sviluppare il progetto.

### <a name="document-level-solutions"></a>Soluzioni a livello di documento
 Il percorso completo di un documento deve essere aggiunto all'elenco di percorsi attendibili nell'applicazione Microsoft Office se si stanno sviluppando i tipi di progetti seguenti:

- Soluzioni a livello di documento in una condivisione file di rete, ad esempio *\\ \nomeserver\nomecondizione*.

- Soluzioni a livello di documento per Word che *usano.doc* o *docm.*

  Includere le sottodirectory quando si aggiunge il percorso del documento all'elenco di percorsi attendibili oppure includere le cartelle di debug e di compilazione specifiche. Per altre informazioni, vedere l'Microsoft Office guida online creare, rimuovere o modificare un [percorso attendibile per i file](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

### <a name="temporary-certificates"></a>Certificati temporanei
 Se non è disponibile un certificato di firma, Visual Studio crea un certificato temporaneo. Usare questo certificato temporaneo solo durante lo sviluppo e acquistare un certificato ufficiale per la distribuzione.

 Il certificato temporaneo viene generato dopo la prima compilazione di un progetto Office. La volta successiva che si preme **F5,** il progetto viene ricompilato perché il progetto viene contrassegnato come modificato quando viene aggiunto il certificato.

 Cancellare regolarmente i certificati temporanei poiché potrebbero accumularsi nel tempo.

## <a name="visual-studio-tools-for-office-runtime"></a><a name="VisualStudioToolsForOfficeRuntime"></a>Visual Studio Tools per Office runtime
 dispone [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] di funzionalità per verificare l'identità del server di pubblicazione e le autorizzazioni concesse a una personalizzazione. Verifica le autorizzazioni mediante una sequenza di controlli di sicurezza.

### <a name="security-during-customization-loading"></a>Sicurezza durante il caricamento della personalizzazione
 Quando viene caricata una personalizzazione a livello di documento, controlla sempre se [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] il documento si trova nell'elenco di percorsi attendibili. Inoltre, il runtime controlla se la soluzione richiede FullTrust nel manifesto dell'applicazione. Non esegue controlli di sicurezza aggiuntivi durante il caricamento della personalizzazione.

### <a name="sequence-of-security-checks-during-installation"></a>Sequenza dei controlli di sicurezza durante l'installazione
 Quando una soluzione Office viene installata o aggiornata, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] esegue un set di controlli di sicurezza in una sequenza specifica per prendere una decisione di attendibilità. Una soluzione viene installata o aggiornata solo se il runtime ne determina l'attendibilità.

 È possibile avviare il processo di installazione in uno dei quattro modi seguenti: eseguendo il programma di installazione, aprendo il manifesto della distribuzione, aprendo l'host dell'applicazione Microsoft Office o eseguendo *VSTOInstaller.exe*.

 Il primo controllo di sicurezza si applica solo alle soluzioni a livello di documento. Il documento di una soluzione a livello di documento deve trovarsi in un percorso attendibile. Se il documento si trova in una condivisione file di rete remota o ha *un'estensione.doc* o *docm,* il percorso del documento deve essere aggiunto all'elenco dei percorsi attendibili. Per altre informazioni, vedere [Concedere l'attendibilità ai documenti.](../vsto/granting-trust-to-documents.md)

 ![Sicurezza VSTO: installazione da Microsoft Office](../vsto/media/host-install.png "Sicurezza VSTO: installazione da Microsoft Office")

 Il set di controlli di sicurezza successivo è quello di [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] e ClickOnce. Per superare questi controlli, le soluzioni Office devono richiedere le autorizzazioni FullTrust, essere firmate da un certificato non compreso nell'elenco degli editori non attendibili e trovarsi in un percorso non incluso nell'area con restrizioni di Internet Explorer. Se il certificato si trova nell'elenco degli editori attendibili, la soluzione viene installata immediatamente. In caso contrario, se ha superato i controlli, la soluzione continua con l'ultimo set di controlli.

 ![Sicurezza VSTO per l'installazione di soluzioni](../vsto/media/installing.png "Sicurezza VSTO per l'installazione di soluzioni")

 Se la richiesta di attendibilità è consentita e alla soluzione non è ancora stata concessa l'attendibilità, il runtime consentirà all'utente finale di prendere [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] la decisione di attendibilità. Se l'utente concede l'attendibilità alla soluzione, viene aggiunta una voce all'elenco di inclusione dell'utente. Tutte le soluzioni nell'elenco di inclusione dell'utente hanno l'attendibilità totale e possono essere installate ed eseguite.

 A partire da Visual Studio 2010, l'elenco di inclusione viene ignorato se la soluzione Office viene installata usando Windows Installer (MSI) nella directory Programmi. Per altre informazioni, vedere [Trust Office solutions by using inclusion lists](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![Sicurezza VSTO: utilizzo del Programma di installazione per effettuare l'installazione](../vsto/media/setup-vstoinstaller.png "Sicurezza VSTO: utilizzo del Programma di installazione per effettuare l'installazione")

## <a name="see-also"></a>Vedi anche

- [Concedere l'attendibilità Office soluzioni](../vsto/granting-trust-to-office-solutions.md)
- [Concedere l'attendibilità ai documenti](../vsto/granting-trust-to-documents.md)
- [Soluzioni Office attendibilità tramite elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Procedura: Configurare la sicurezza dell'elenco di inclusione](../vsto/how-to-configure-inclusion-list-security.md)
- [Procedura: Firmare Office soluzioni](../vsto/how-to-sign-office-solutions.md)
- [Risolvere i Office della soluzione](../vsto/troubleshooting-office-solution-security.md)
- [Manifesti dell'applicazione per Office soluzioni](../vsto/application-manifests-for-office-solutions.md)
- [Manifesti di distribuzione per Office soluzioni](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce informazioni di riferimento](../deployment/clickonce-reference.md)
- [Distribuire una soluzione Office distribuzione](../vsto/deploying-an-office-solution.md)
