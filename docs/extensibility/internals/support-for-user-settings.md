---
title: Supporto per User Impostazioni | Microsoft Docs
description: Informazioni su come abilitare la persistenza delle categorie di impostazioni usando le API delle impostazioni in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d317809bde56132f990c11e641ae151fcbac8eff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086508"
---
# <a name="support-for-user-settings"></a>Supporto per le impostazioni utente
Un PACCHETTO VSPackage può definire una o più categorie di impostazioni, ovvero  gruppi di variabili di stato persistenti quando un utente sceglie il comando Importazione/Esportazione Impostazioni dal **menu** Strumenti. Per abilitare questa persistenza, usare le API delle impostazioni in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 Una voce del Registro di sistema definita punto di Impostazioni personalizzato e un GUID definisce la categoria di impostazioni di un VSPackage. Un PACCHETTO VSPackage può supportare più categorie di impostazioni, ognuna definita da un punto Impostazioni personalizzato.

- Le implementazioni di impostazioni basate su assembly di interoperabilità (tramite l'interfaccia ) devono creare un punto di Impostazioni personalizzato modificando il Registro di sistema o usando uno script registrar (file con estensione <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> rgs). Per altre informazioni, vedere [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Il codice che usa Managed Package Framework (MPF) deve creare punti di Impostazioni personalizzati allegando un al pacchetto VSPackage per ogni <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> punto Impostazioni personalizzato.

     Se un singolo VSPackage supporta diversi punti Impostazioni personalizzati, ogni punto Impostazioni personalizzato viene implementato da una classe separata e ognuno viene registrato da un'istanza univoca della <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe. Di conseguenza, una classe di implementazione delle impostazioni può supportare più di una categoria di impostazioni.

## <a name="custom-settings-point-registry-entry-details"></a>Dettagli delle voci Impostazioni punto di accesso personalizzato
 I punti Impostazioni personalizzati vengono creati in una voce del Registro di sistema nel percorso seguente: HKLM\Software\Microsoft\VisualStudio \UserSettings , dove è il nome del punto Impostazioni personalizzato che il vspackage supporta e è la versione di , ad esempio \\ *\<Version>* \\ `<CSPName>` `<CSPName>` *\<Version>* [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8.0.

> [!NOTE]
> Il percorso radice dellHKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudiopuò essere sottoposto a override con una radice alternativa quando viene inizializzato \\ *\<Version>* l'ambiente di sviluppo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrato (IDE). Per altre informazioni, vedere [Opzioni della riga di comando.](../../extensibility/command-line-switches-visual-studio-sdk.md)

 La struttura della voce del Registro di sistema è illustrata di seguito:

 HKLM\Software\Microsoft\VisualStudio \\ *\<Version>* \UserSettings\

 `<CSPName`>= '#12345'

 Package = '{XXXXXX XXXX XXXX XXXX XXXXXXXXX}'

 Category = '{YYYYYY YYYY YYYY YYYY YYYYY}'

 ResourcePackage = '{ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZ}'

 AlternateParent = CategoryName

| Nome | Tipo | Dati | Descrizione |
|-----------------|--------| - | - |
| Valore predefinito. | REG_SZ | Nome del punto Impostazioni personalizzato | Il nome della chiave,>, è il nome non localizzato del `<CSPName` punto Impostazioni personalizzato.<br /><br /> Per le implementazioni basate su MPF, il nome della chiave viene ottenuto combinando gli `categoryName` argomenti e del costruttore in `objectName` <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `categoryName_objectName` .<br /><br /> La chiave può essere vuota o può contenere l'ID di riferimento alla stringa localizzata in una DLL satellite. Questo valore viene ottenuto `objectNameResourceID` dall'argomento al <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> costruttore . |
| Pacchetto | REG_SZ | GUID | GUID del pacchetto VSPackage che implementa il punto Impostazioni personalizzato.<br /><br /> Le implementazioni basate su MPF che usano la classe usano l'argomento del costruttore contenente il vspackage e <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> la reflection per ottenere questo `objectType` <xref:System.Type> valore. |
| Category | REG_SZ | GUID | GUID che identifica la categoria di impostazioni.<br /><br /> Per le implementazioni basate su assembly di interoperabilità, questo valore può essere un GUID scelto arbitrariamente, che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'IDE passa ai metodi e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> . Tutte le implementazioni di questi due metodi devono verificare i relativi argomenti GUID.<br /><br /> Per le implementazioni basate su MPF, questo GUID viene ottenuto dalla <xref:System.Type> classe che implementa il meccanismo delle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] impostazioni. |
| ResourcePackage | REG_SZ | GUID | facoltativo.<br /><br /> Percorso della DLL satellite contenente le stringhe localizzate se il pacchetto VSPackage di implementazione non le fornisce.<br /><br /> MPF usa la reflection per ottenere il pacchetto VSPackage di risorsa corretto, quindi <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> la classe non imposta questo argomento. |
| AlternateParent | REG_SZ | Nome della cartella nella pagina Opzioni strumenti contenente questo punto di Impostazioni personalizzato. | facoltativo.<br /><br /> È necessario impostare questo valore solo  se un'implementazione delle impostazioni supporta le pagine Opzioni degli strumenti che usano il meccanismo di persistenza in anziché il meccanismo nel modello di automazione per [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] salvare lo stato.<br /><br /> In questi casi, il valore nella chiave AlternateParent è la sezione della stringa usata `topic` per identificare la pagina `topic.sub-topic` **ToolsOptions** specifica. Ad esempio, per la **pagina StrumentiOpzioni** `"TextEditor.Basic"` il valore di AlternateParent sarà `"TextEditor"` .<br /><br /> Quando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> genera il punto Impostazioni personalizzato, corrisponde al nome della categoria. |
