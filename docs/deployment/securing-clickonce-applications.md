---
title: Protezione delle applicazioni ClickOnce | Microsoft Docs
description: Informazioni sulle implicazioni dei vincoli di sicurezza dall'accesso di codice nel .NET Framework che possono limitare l'accesso al codice per le ClickOnce applicazioni.
ms.custom: SEO-VS-2020
ms.date: 02/17/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 722e37cf87256d6b1e95232228d2ae4357075618
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627749"
---
# <a name="secure-clickonce-applications"></a>Proteggere le applicazioni ClickOnce
Le applicazioni[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono soggette ai vincoli di sicurezza dall'accesso di codice in .NET Framework che consentono di limitare l'accesso del codice alle risorse e alle operazioni protette. Per poter scrivere correttamente le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , è quindi importante comprendere le implicazioni di questo tipo di sicurezza. Le applicazioni possono usare l'attendibilità totale o le aree parziali, ad esempio le aree Internet e Intranet, per limitare l'accesso.

 Inoltre, ClickOnce usa i certificati per verificare l'autenticità dell'editore dell'applicazione e per firmare i manifesti dell'applicazione e della distribuzione al fine di dimostrare che i file non sono stati alterati. La firma è un passaggio facoltativo, che semplifica la modifica dei file dell'applicazione dopo la generazione dei manifesti. Senza manifesti firmati, è tuttavia difficile garantire che il programma di installazione dell'applicazione non venga manomesso in attacchi alla sicurezza di tipo man-in-the-middle. Per questo motivo, è consigliabile firmare i manifesti dell'applicazione e della distribuzione per proteggere le applicazioni.

## <a name="zones"></a>Zone
 Le applicazioni distribuite con la tecnologia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sono limitate a un set di autorizzazioni e azioni definite dall'area di sicurezza. Le aree di sicurezza vengono definite in Internet Explorer e si basano sul percorso dell'applicazione. Nella seguente tabella sono elencate le autorizzazioni predefinite in base al percorso di distribuzione:

|Percorso di distribuzione|Area di sicurezza|
|-------------------------|-------------------|
|Esecuzione dal Web|Area Internet|
|Installazione dal Web|Area Internet|
|Installazione da una condivisione file in rete|Area Intranet locale|
|Installazione da CD|Attendibilità totale|

 Le autorizzazioni predefinite dipendono dal percorso di distribuzione della versione originale dell'applicazione. Gli eventuali aggiornamenti erediteranno tali autorizzazioni. Se l'applicazione è configurata in modo da controllare la disponibilità degli aggiornamenti in un percorso Web o di rete e viene rilevata la disponibilità di una versione più recente, è possibile che l'installazione originale riceva autorizzazioni per l'area Internet o Intranet anziché autorizzazioni di attendibilità totale. Per evitare che la richiesta venga visualizzata, l'amministratore di sistema può specificare criteri di distribuzione ClickOnce che definiscano uno specifico editore dell'applicazione come fonte attendibile. Per i computer in cui viene distribuito questi criteri, le autorizzazioni verranno concesse automaticamente senza alcun intervento da parte dell'utente. Per altre informazioni, vedere [Cenni preliminari sulla distribuzione di applicazioni attendibili.](../deployment/trusted-application-deployment-overview.md) Per configurare la distribuzione di applicazioni attendibili, è possibile installare il certificato nel computer o a livello aziendale. Per altre informazioni, vedere [procedura: aggiungere un autore attendibile a un Computer Client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md).

## <a name="code-access-security-policies"></a>Criteri di sicurezza per l'accesso al codice
 Le autorizzazioni per un'applicazione sono determinate dalle impostazioni [ \<trustInfo> nell'elemento Element](../deployment/trustinfo-element-clickonce-application.md) del manifesto dell'applicazione. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera automaticamente queste informazioni in base alle impostazioni nella pagina delle proprietà **Sicurezza** del progetto. A un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vengono concesse solo le autorizzazioni specifiche richieste. Ad esempio, se per l'accesso ai file sono necessarie autorizzazioni di attendibilità totale, ma l'applicazione richiede solo l'autorizzazione di accesso ai file, verrà concessa solo questa autorizzazione e non quelle di attendibilità totale. Quando si sviluppa l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , è necessario assicurarsi di richiedere solo le autorizzazioni specifiche necessarie per l'applicazione. Nella maggior parte dei casi è possibile usare le aree Internet o Intranet locale per limitare l'applicazione a un'attendibilità parziale. Per altre informazioni, vedere [Procedura: Impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md). Se l'applicazione richiede autorizzazioni personalizzate, è possibile creare un'area personalizzata. Per altre informazioni, vedere [Procedura: Impostare autorizzazioni personalizzate](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)per un'ClickOnce applicazione .

 Se si aggiunge un'autorizzazione non inclusa nel set di autorizzazioni predefinito per l'area da cui viene distribuita l'applicazione, all'utente finale verrà chiesto di concedere l'autorizzazione al momento dell'installazione o dell'aggiornamento. Per evitare che la richiesta venga visualizzata, l'amministratore di sistema può specificare criteri di distribuzione ClickOnce che definiscano uno specifico editore dell'applicazione come fonte attendibile. Sui computer in cui vengono distribuiti questi criteri, le autorizzazioni verranno concesse automaticamente senza alcun intervento da parte dell'utente.

 Uno sviluppatore ha la responsabilità di assicurarsi che l'applicazione venga eseguita con le autorizzazioni appropriate. Se l'applicazione richiede autorizzazioni all'esterno di un'area durante il run-time, è possibile che venga visualizzata un'eccezione di sicurezza. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di eseguire il debug dell'applicazione nell'area di sicurezza di destinazione e fornisce assistenza per lo sviluppo di applicazioni sicure. Per altre informazioni, vedere [Eseguire il debug ClickOnce che usano System.Deployment.Application.](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)

 Per altre informazioni sulla sicurezza per l'accesso al codice e su ClickOnce, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).

## <a name="code-signing-certificates"></a>Certificati per la firma del codice
 Per pubblicare un'applicazione tramite la tecnologia di distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , è possibile firmare il manifesto dell'applicazione e della distribuzione con una coppia di chiavi pubblica/privata. Gli strumenti per firmare un manifesto sono disponibili nella pagina **Firma** di **Progettazione progetti**. Per altre informazioni, vedere [Signing Page, Project Designer](../ide/reference/signing-page-project-designer.md).

 Durante l'installazione, dopo la firma dei manifesti, nella finestra di dialogo Autorizzazioni verranno visualizzate le informazioni sull'editore basate sulla firma Authenticode, per dimostrare all'utente che l'applicazione proviene da una fonte attendibile.

 Per altre informazioni su ClickOnce e sui certificati, vedere [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md).

## <a name="aspnet-form-based-authentication"></a>Autenticazione basata su form ASP.NET
 Per controllare le distribuzioni cui può accedere ciascun utente, è consigliabile non consentire l'accesso anonimo alle applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuite su un server Web. La soluzione migliore consiste nel concedere agli utenti l'accesso alle distribuzioni installate in base all'identità, usando l'autenticazione di Windows.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] non supporta l'autenticazione basata su form ASP.NET perché prevede l'uso di cookie permanenti. Questi comportano un rischio di sicurezza in quanto rimangono nella cache di Internet Explorer e sono quindi vulnerabili ad attacchi di pirateria. Se pertanto si distribuiscono applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , non è supportato alcuno scenario di autenticazione ad eccezione dell'autenticazione di Windows.

## <a name="pass-arguments"></a>Passaggio di argomenti
 Se è necessario passare argomenti a un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , è opportuno valutare altre implicazioni sulla sicurezza. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] consente agli sviluppatori di fornire una stringa di query alle applicazioni distribuite sul Web. La stringa di query è una serie di coppie nome/valore aggiunte alla fine dell'URL usato per avviare l'applicazione:

 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`

 Gli argomenti delle stringhe di query sono disabilitati per impostazione predefinita. Per attivarli, nel manifesto di distribuzione dell'applicazione deve essere impostato l'attributo `trustUrlParameters` . Questo valore può essere impostato da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e da MageUI.exe. Per istruzioni dettagliate su come abilitare il passaggio di stringhe di query, vedere [Procedura: Recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

 Non passare mai argomenti recuperati tramite una stringa di query direttamente a un database o alla riga di comando senza verificare che gli argomenti siano sicuri. Sono considerati non sicuri gli argomenti che includono caratteri di escape di database o da riga di comando che possono consentire a un utente malintenzionato di modificare l'applicazione eseguendo comandi arbitrari.

> [!NOTE]
> Gli argomenti delle stringhe di query sono l'unico modo per passare argomenti a un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] all'avvio. Non è possibile passare argomenti a un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dalla riga di comando.

## <a name="deploying-obfuscated-assemblies"></a>Distribuzione di assembly offuscati
 Visual Studio include la versione gratuita di [PreEmptive Protection - Dotfuscator Community](../ide/dotfuscator/index.md), che è possibile usare per proteggere le applicazioni ClickOnce tramite l'offuscamento del codice e misure di protezione attive.  Per informazioni dettagliate, vedere [la sezione dedicata a ClickOnce della guida dell'utente di Dotfuscator Community](https://www.preemptive.com/dotfuscator/ce/docs/help/5.27/advanced_clickonce.html).

## <a name="see-also"></a>Vedi anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
