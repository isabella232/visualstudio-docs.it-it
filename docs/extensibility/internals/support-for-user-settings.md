---
title: Supporto per le impostazioni utente Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704783"
---
# <a name="support-for-user-settings"></a>Supporto per le impostazioni utente
Un pacchetto VSPackage può definire una o più categorie di impostazioni, ovvero gruppi di variabili di stato che vengono mantenute quando un utente sceglie il comando **Importa/Esporta impostazioni** dal menu **Strumenti.** Per abilitare questa persistenza, utilizzare le [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]API delle impostazioni nel file .

 Una voce del Registro di sistema che viene definita un punto di impostazioni personalizzate e un GUID definisce la categoria di impostazioni di un VSPackage.A registry entry that is referred to as a Custom Settings Point and a GUID defines a VSPackage's settings category. Un VSPackage può supportare più categorie di impostazioni, ognuna definita da un punto di impostazioni personalizzate.

- Le implementazioni delle impostazioni basate su <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> assembly di interoperabilità (utilizzando l'interfaccia) devono creare un punto di impostazioni personalizzate modificando il Registro di sistema o utilizzando uno script di registrazione (file RGS). Per altre informazioni, vedere [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

- Il codice che usa Managed Package Framework (MPF) deve <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> creare punti di impostazioni personalizzate collegando un al pacchetto VSPackage per ogni punto di impostazioni personalizzate.

     Se un singolo VSPackage supporta diversi punti di impostazioni personalizzate, ogni punto di impostazioni personalizzate viene <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> implementato da una classe separata e ognuno viene registrato da un'istanza univoca della classe. Di conseguenza, una classe di implementazione delle impostazioni può supportare più di una categoria di impostazioni.

## <a name="custom-settings-point-registry-entry-details"></a>Dettagli voce del Registro di sistema di impostazioni personalizzate
 I punti delle impostazioni personalizzate vengono creati in una voce del Registro di sistema\\`<CSPName>`nel `<CSPName>` seguente percorso: HKLM, Software, Microsoft VisualStudio\\*\<Version * [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]>, dove è il nome del punto di amministrazione delle impostazioni personalizzate supportato da VSPackage e * \<Version>* è la versione di , ad esempio 8.0.

> [!NOTE]
> Quando si inizializza l'ambiente\\ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE), è possibile eseguire l'override del percorso di HKEY_LOCAL_MACHINE>della*\<versione* di VisualStudio. Per ulteriori informazioni, vedere [Opzioni della riga](../../extensibility/command-line-switches-visual-studio-sdk.md)di comando .

 La struttura della voce del Registro di sistema è illustrata di seguito:

 HKLM Software Microsoft VisualStudio\\*\<Versione>* Impostazioni utente

 `<CSPName`>'#12345'

 Pacchetto: ''XXXXXX XXXX XXXX XXXXXXXXX''

 Categoria : ' AAAAA AAAA AAAA AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'

 Pacchetto Di Risorse , Sz . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

 AlternateParent - CategoryName

| Nome | Type | Data | Descrizione |
|-----------------|--------| - | - |
| Valore predefinito. | REG_SZ | Nome del punto delle impostazioni personalizzate | Il nome della `<CSPName` chiave,>, è il nome non localizzato del punto di impostazioni personalizzate.<br /><br /> Per le implementazioni basate su MPF, il nome `categoryName` `objectName` della chiave <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> viene `categoryName_objectName`ottenuto combinando gli argomenti e del costruttore in .<br /><br /> La chiave può essere vuota oppure può contenere l'ID di riferimento alla stringa localizzata in una DLL satellite. Questo valore viene `objectNameResourceID` ottenuto <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> dall'argomento al costruttore. |
| Pacchetto | REG_SZ | GUID | GUID del pacchetto VSPackage che implementa il punto di impostazioni personalizzate.<br /><br /> Implementazioni basate su MPF utilizzando la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe `objectType` , utilizzare l'argomento del costruttore contenente il VSPackage <xref:System.Type> e la reflection per ottenere questo valore. |
| Category | REG_SZ | GUID | GUID che identifica la categoria di impostazioni.<br /><br /> Per le implementazioni basate su assembly di interoperabilità, questo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] valore può <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> essere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> un GUID scelto arbitrariamente, che l'IDE passa ai metodi e . Tutte le implementazioni di questi due metodi devono verificare i relativi argomenti GUID.<br /><br /> Per le implementazioni basate su MPF, <xref:System.Type> questo GUID [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene ottenuto dalla classe che implementa il meccanismo delle impostazioni. |
| ResourcePackage | REG_SZ | GUID | Facoltativa.<br /><br /> Percorso della DLL satellite contenente le stringhe localizzate se l'oggetto VSPackage di implementazione non le fornisce.<br /><br /> MPF utilizza la reflection per ottenere la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> risorsa corretta VSPackage, in modo che la classe non imposta questo argomento. |
| Elemento padre alternativo | REG_SZ | Nome della cartella nella pagina Opzioni strumenti contenente questo punto di impostazioni personalizzate. | Facoltativa.<br /><br /> È necessario impostare questo valore solo se un'implementazione delle [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] impostazioni supporta le pagine Opzioni **degli** strumenti che utilizzano il meccanismo di persistenza nel meccanismo anziché nel meccanismo nel modello di automazione per salvare lo stato.<br /><br /> In questi casi, il valore nella `topic` chiave AlternateParent è la sezione della `topic.sub-topic` stringa utilizzata per identificare la pagina **ToolsOptions** specifica. Ad esempio, per la `"TextEditor.Basic"` pagina **ToolsOptions** il `"TextEditor"`valore di AlternateParent sarà .<br /><br /> Quando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> genera il punto di impostazioni personalizzate, è lo stesso del nome della categoria. |
