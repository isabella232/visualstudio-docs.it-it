---
title: Impostazioni dell'applicazione e ClickOnce | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a72b5bc3f3645d9af1008f2c178ab285e8b45449
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184133"
---
# <a name="clickonce-and-application-settings"></a>Impostazioni dell'applicazione e ClickOnce
Le impostazioni dell'applicazione per Windows Forms semplificano la creazione, l'archiviazione e la gestione delle preferenze personalizzate dell'applicazione e dell'utente nel client. Nel documento seguente viene descritto il funzionamento dei file di impostazioni dell'applicazione in un'applicazione ClickOnce e il modo in cui ClickOnce migra le impostazioni quando l'utente effettua l'aggiornamento alla versione successiva.

 Le informazioni riportate di seguito si applicano solo al provider di impostazioni dell'applicazione predefinito, ovvero la <xref:System.Configuration.LocalFileSettingsProvider> classe. Se si fornisce un provider personalizzato, il provider determinerà il modo in cui archivia i dati e il modo in cui aggiorna le impostazioni tra le versioni. Per altre informazioni sui provider di impostazioni dell'applicazione, vedere [architettura delle impostazioni dell'applicazione](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>File di impostazioni dell'applicazione
 Le impostazioni dell'applicazione utilizzano due file: * \<app> . exe. config* e *User. config*, dove *app* è il nome della Windows Forms Application. *User. config* viene creato nel client la prima volta che l'applicazione archivia le impostazioni con ambito di utente. * \<app> . exe. config*, al contrario, sarà presente prima della distribuzione se si definiscono i valori predefiniti per le impostazioni. Il file verrà incluso automaticamente in Visual Studio quando si usa il relativo comando di **pubblicazione** . Se si crea l'applicazione ClickOnce con *Mage. exe* o *MageUI. exe*, è necessario assicurarsi che questo file sia incluso negli altri file dell'applicazione quando si popola il manifesto dell'applicazione.

 In una Windows Forms Application non distribuita mediante ClickOnce, il file con * \<app> estensione exe. config* di un'applicazione viene archiviato nella directory dell'applicazione, mentre il file *User. config* è archiviato nella cartella **Documents and Settings** dell'utente. In un'applicazione ClickOnce, * \<app> exe. config* si trova nella directory dell'applicazione all'interno della cache dell'applicazione ClickOnce e *User. config* risiede nella directory dei dati ClickOnce dell'applicazione.

 Indipendentemente dalla modalità di distribuzione dell'applicazione, le impostazioni dell'applicazione garantiscono l'accesso in lettura sicuro a * \<app> . exe. config*e l'accesso in lettura/scrittura sicuro a *User. config*.

 In un'applicazione ClickOnce, le dimensioni dei file di configurazione utilizzati dalle impostazioni dell'applicazione sono limitate dalle dimensioni della cache ClickOnce. Per altre informazioni, vedere [Panoramica della cache ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Aggiornamenti della versione
 Così come ogni versione di un'applicazione ClickOnce è isolata da tutte le altre versioni, le impostazioni dell'applicazione per un'applicazione ClickOnce sono isolate dalle impostazioni anche per le altre versioni. Quando l'utente esegue l'aggiornamento a una versione successiva dell'applicazione, le impostazioni dell'applicazione confrontano le impostazioni della versione più recente (con il numero più elevato) rispetto alle impostazioni fornite con la versione aggiornata e unisce le impostazioni in un nuovo set di file di impostazioni.

 Nella tabella seguente viene descritto in che modo le impostazioni dell'applicazione decidono le impostazioni da copiare.

|Tipo di modifica|Azione di aggiornamento|
|--------------------|--------------------|
|Impostazione aggiunta a * \<app> . exe. config*|La nuova impostazione viene unita nel * \<app> file. exe. config* della versione corrente|
|Impostazione rimossa da * \<app> . exe. config*|L'impostazione precedente viene rimossa dal * \<app> file. exe. config* della versione corrente|
|Impostazione predefinita dell'impostazione modificata; impostazione locale ancora impostata sul valore predefinito originale in *User. config*|L'impostazione viene unita al *file User. config* della versione corrente con il nuovo valore predefinito|
|Impostazione predefinita dell'impostazione modificata; impostazione impostata su non predefinita in *User. config*|L'impostazione viene unita al *file User. config* della versione corrente con il valore non predefinito mantenuto|

Se è stata creata la classe wrapper delle impostazioni dell'applicazione e si desidera personalizzare la logica di aggiornamento, è possibile eseguire l'override del <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> metodo.

## <a name="clickonce-and-roaming-settings"></a>Impostazioni di ClickOnce e roaming
 ClickOnce non funziona con le impostazioni di roaming, consentendo al file di impostazioni di seguire le varie macchine in una rete. Se sono necessarie impostazioni di roaming, sarà necessario implementare un provider di impostazioni dell'applicazione che archivia le impostazioni in rete o sviluppare classi di impostazioni personalizzate per archiviare le impostazioni in un computer remoto. Per altre informazioni sui provider di impostazioni, vedere [architettura delle impostazioni dell'applicazione](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Vedere anche
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Cenni preliminari sulle impostazioni delle applicazioni](/dotnet/framework/winforms/advanced/application-settings-overview)
- [Panoramica della cache di ClickOnce](../deployment/clickonce-cache-overview.md)
- [Accedere a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)