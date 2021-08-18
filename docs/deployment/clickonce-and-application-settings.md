---
title: ClickOnce e application Impostazioni | Microsoft Docs
description: Informazioni sul funzionamento dei file di impostazioni dell'applicazione in un'applicazione ClickOnce e su come ClickOnce le impostazioni quando l'utente esegue l'aggiornamento alla versione successiva.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 2e321f905e4bad8139705b8f9bcb6139c5d10a9c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051651"
---
# <a name="clickonce-and-application-settings"></a>Impostazioni dell'applicazione e ClickOnce
Le impostazioni dell'Windows forms semplificano la creazione, l'archiviazione e la gestione delle preferenze utente e dell'applicazione personalizzate nel client. Il documento seguente descrive il funzionamento dei file di impostazioni dell'applicazione in un'applicazione ClickOnce e ClickOnce esegue la migrazione delle impostazioni quando l'utente esegue l'aggiornamento alla versione successiva.

 Le informazioni seguenti si applicano solo al provider di impostazioni dell'applicazione predefinito, la <xref:System.Configuration.LocalFileSettingsProvider> classe . Se si specifica un provider personalizzato, tale provider determinerà il modo in cui archivia i dati e come aggiorna le impostazioni tra le versioni. Per altre informazioni sui provider di impostazioni dell'applicazione, vedere [Architettura delle impostazioni dell'applicazione](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>File di impostazioni dell'applicazione
 Le impostazioni dell'applicazione utilizzano due file: *\<app>.exe.config* *euser.config*, dove *app* è il nome dell'applicazione Windows Forms. *user.config* viene creato nel client la prima volta che l'applicazione archivia le impostazioni con ambito utente. *\<app>.exe.config,* invece, esisterà prima della distribuzione se si definiscono i valori predefiniti per le impostazioni. Visual Studio questo file verrà incluso automaticamente quando si usa il **comando Pubblica.** Se si crea l'applicazione ClickOnce usando *Mage.exe* o *MageUI.exe*, è necessario assicurarsi che questo file sia incluso con gli altri file dell'applicazione quando si popola il manifesto dell'applicazione.

 In un'applicazione Windows Forms non distribuita tramite ClickOnce, il file *\<app>.exe.config* di un'applicazione viene archiviato nella directory dell'applicazione, mentre il file *user.config* viene archiviato nella cartella **Documents and Impostazioni** dell'utente. In un'applicazione ClickOnce, *\<app>.exe.config* si trova nella directory dell'applicazione all'interno della cache dell'applicazione ClickOnce e *user.config* si trova nella directory dei dati ClickOnce per tale applicazione.

 Indipendentemente dalla modalità di distribuzione dell'applicazione, le impostazioni dell'applicazione assicurano l'accesso *\<app> in* lettura sicuro.exe.confige l'accesso sicuro in lettura/scrittura *auser.config*.

 In un ClickOnce appalto, le dimensioni dei file di configurazione usati dalle impostazioni dell'applicazione sono vincolate dalle dimensioni della cache ClickOnce dati. Per altre informazioni, vedere panoramica ClickOnce [cache.](../deployment/clickonce-cache-overview.md)

## <a name="version-upgrades"></a>Aggiornamenti della versione
 Come ogni versione di un'applicazione ClickOnce è isolata da tutte le altre versioni, le impostazioni dell'applicazione per un'applicazione ClickOnce sono isolate dalle impostazioni anche per altre versioni. Quando l'utente esegue l'aggiornamento a una versione successiva dell'applicazione, le impostazioni dell'applicazione confrontano le impostazioni della versione più recente (con il numero più alto) con le impostazioni fornite con la versione aggiornata e uniscono le impostazioni in un nuovo set di file di impostazioni.

 La tabella seguente descrive come le impostazioni dell'applicazione decidono quali impostazioni copiare.

|Tipo di modifica|Azione di aggiornamento|
|--------------------|--------------------|
|Impostazione aggiunta a *\<app>.exe.config*|La nuova impostazione viene unita alla versione *\<app> corrente*.exe.config|
|Impostazione rimossa *\<app> da.exe.config*|L'impostazione precedente viene rimossa dalla versione *\<app> corrente*.exe.config|
|L'impostazione predefinita è stata modificata. l'impostazione locale è ancora impostata sul valore predefinito *originaleuser.config*|L'impostazione viene unita alla versione correnteuser.config *con* il nuovo valore predefinito come valore|
|L'impostazione predefinita è stata modificata. impostazione impostata su non predefinita in *user.config*|L'impostazione viene unita alla versione correnteuser.config *con* il valore non predefinito mantenuto|

Se è stata creata la propria classe wrapper delle impostazioni dell'applicazione e si vuole personalizzare la logica di aggiornamento, è possibile eseguire l'override del <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> metodo .

## <a name="clickonce-and-roaming-settings"></a>ClickOnce e roaming
 ClickOnce non funziona con le impostazioni mobili, che consentono al file di impostazioni di seguire l'utente tra computer in una rete. Se sono necessarie impostazioni mobili, è necessario implementare un provider di impostazioni dell'applicazione che archivia le impostazioni in rete o sviluppare classi di impostazioni personalizzate per l'archiviazione delle impostazioni in un computer remoto. Per altre informazioni nei provider di impostazioni, vedere [Architettura delle impostazioni dell'applicazione](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Vedi anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Panoramica delle impostazioni dell'applicazione](/dotnet/framework/winforms/advanced/application-settings-overview)
- [Panoramica della cache di ClickOnce](../deployment/clickonce-cache-overview.md)
- [Accedere a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)