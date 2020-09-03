---
title: Supporto per le impostazioni utente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02bb2450196de76917e9cffc2f5f5acc6c8ee7b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704783"
---
# <a name="support-for-user-settings"></a>Supporto per le impostazioni utente
Un pacchetto VSPackage può definire una o più categorie di impostazioni, ovvero gruppi di variabili di stato che vengono mantenute quando un utente sceglie il comando **Importa/Esporta impostazioni** dal menu **strumenti** . Per abilitare questa persistenza, è possibile utilizzare le API delle impostazioni in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 Una voce del registro di sistema denominata punto di impostazioni personalizzato e un GUID definiscono la categoria di impostazioni di un VSPackage. Un pacchetto VSPackage può supportare più categorie di impostazioni, ognuna definita da un punto di impostazioni personalizzato.

- Le implementazioni di impostazioni basate su assembly di interoperabilità (mediante l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interfaccia) devono creare punti di impostazioni personalizzati modificando il registro di sistema o utilizzando uno script del registrar (file con estensione RGS). Per altre informazioni, vedere [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Il codice che usa il Framework di pacchetto gestito (MPF) deve creare punti di impostazioni personalizzati connettendosi a un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> VSPackage per ogni punto di impostazioni personalizzato.

     Se un singolo pacchetto VSPackage supporta diversi punti di impostazioni personalizzati, ogni punto di impostazioni personalizzato viene implementato da una classe separata e ogni punto viene registrato da un'istanza univoca della <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe. Di conseguenza, una classe che implementa le impostazioni può supportare più di una categoria di impostazioni.

## <a name="custom-settings-point-registry-entry-details"></a>Dettagli voce del registro di sistema del punto di impostazioni personalizzato
 I punti delle impostazioni personalizzate vengono creati in una voce del registro di sistema nel percorso seguente: \Software\microsoft\visualstudio HKLM \\ *\<Version>* \UserSettings \\ `<CSPName>` , dove `<CSPName>` è il nome del punto di impostazioni personalizzato supportato da Vspackage e *\<Version>* è la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , ad esempio 8,0.

> [!NOTE]
> Il percorso radice di HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* può essere sostituito con una radice alternativa quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene inizializzato il Integrated Development Environment (IDE). Per ulteriori informazioni, vedere [Opzioni della riga di comando](../../extensibility/command-line-switches-visual-studio-sdk.md).

 La struttura della voce del registro di sistema è illustrata di seguito:

 \\ *\<Version>* \UserSettings\ \Software\Microsoft\VisualStudio HKLM

 `<CSPName`>= s'#12345'

 Package =' {XXXXXX XXXX XXXX XXXX XXXXXXXXX}'

 Category =' {YYYYYY aaaa aaaa aaaa YYYYYYYYY}'

 ResourcePackage =' {ZZZZZZ ZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'

 AlternateParent = CategoryName

| Nome | Type | Dati | Descrizione |
|-----------------|--------| - | - |
| Valore predefinito. | REG_SZ | Nome del punto di impostazioni personalizzato | Il nome della chiave, `<CSPName`>, è il nome non localizzato del punto di impostazioni personalizzato.<br /><br /> Per le implementazioni basate su MPF, il nome della chiave viene ottenuto combinando `categoryName` gli `objectName` argomenti e del <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> costruttore in `categoryName_objectName` .<br /><br /> La chiave può essere vuota oppure può contenere l'ID di riferimento per la stringa localizzata in una DLL satellite. Questo valore viene ottenuto dall' `objectNameResourceID` argomento al <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> costruttore. |
| Pacchetto | REG_SZ | GUID | GUID del pacchetto VSPackage che implementa il punto di impostazioni personalizzato.<br /><br /> Implementazioni basate su MPF mediante la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe, utilizzare l'argomento del costruttore `objectType` contenente i pacchetti VSPackage <xref:System.Type> e reflection per ottenere questo valore. |
| Category | REG_SZ | GUID | GUID che identifica la categoria di impostazioni.<br /><br /> Per le implementazioni basate su assembly di interoperabilità, questo valore può essere un GUID scelto arbitrariamente, che l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE passa ai <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> metodi e. Tutte le implementazioni di questi due metodi devono verificarne gli argomenti GUID.<br /><br /> Per le implementazioni basate su MPF, questo GUID viene ottenuto dall'oggetto <xref:System.Type> della classe che implementa il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] meccanismo delle impostazioni. |
| ResourcePackage | REG_SZ | GUID | facoltativo.<br /><br /> Percorso della DLL satellite contenente le stringhe localizzate se il pacchetto VSPackage di implementazione non le fornisce.<br /><br /> MPF usa la reflection per ottenere il pacchetto VSPackage di risorse corretto, pertanto la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe non imposta questo argomento. |
| AlternateParent | REG_SZ | Nome della cartella nella pagina Opzioni degli strumenti contenente il punto di impostazioni personalizzato. | facoltativo.<br /><br /> È necessario impostare questo valore solo se un'implementazione di impostazioni supporta le pagine **Opzioni degli strumenti** che usano il meccanismo di persistenza in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] anziché il meccanismo nel modello di automazione per salvare lo stato.<br /><br /> In questi casi, il valore della chiave AlternateParent è la `topic` sezione della `topic.sub-topic` stringa usata per identificare la pagina **ToolsOptions** specifica. Per la pagina **ToolsOptions** , ad esempio, `"TextEditor.Basic"` il valore di AlternateParent sarà `"TextEditor"` .<br /><br /> Quando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> genera il punto di impostazioni personalizzato, corrisponde al nome della categoria. |
