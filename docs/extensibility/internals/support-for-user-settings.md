---
title: Supporto per le impostazioni utente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Custom Settings Points
- user settings [Visual Studio SDK], registering persistence support
- persistence, registering settings
ms.assetid: ad9beac3-4f8d-4093-ad0e-6fb00444a709
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c358f80284083625dfe8c0eb3484c95000beb63
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670446"
---
# <a name="support-for-user-settings"></a>Supporto per le impostazioni utente
Un pacchetto VSPackage può definire uno o più categorie di impostazioni, che sono gruppi di variabili di stato che rendono persistenti quando un utente sceglie il **Importa/Esporta impostazioni** comando le **Tools** menu. Per abilitare la persistenza, si usano le impostazioni API nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

 Una voce del Registro di sistema che si intende un punto di impostazioni personalizzato e un GUID definisce la categoria di impostazioni di VSPackage. Un pacchetto VSPackage può supportare più categorie di impostazioni, ognuno definito da un punto di impostazioni personalizzato.

-   Le implementazioni di impostazioni che si basano sugli assembly di interoperabilità (usando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> interface) devono creare punto di impostazioni personalizzato modificando il Registro di sistema o utilizzando uno script di registrazione (file con estensione RGS). Per altre informazioni, vedere [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

-   Codice che usa il Framework di pacchetto gestito (MPF) debba creare punti di impostazioni personalizzati collegando un <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> a VSPackage per ogni punto di impostazioni personalizzato.

     Se un pacchetto VSPackage singolo supporta diversi punti di impostazioni personalizzati, ogni punto di impostazioni personalizzato viene implementato da una classe distinta e ciascuno viene registrato da un'istanza univoca del <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe. Di conseguenza, le impostazioni di implementazione della classe possono supportare più di una categoria di impostazioni.

## <a name="custom-settings-point-registry-entry-details"></a>Dettagli delle voci del Registro di sistema di punto di impostazioni personalizzate
 Punti di impostazioni personalizzati vengono creati in una voce del Registro di sistema nel percorso seguente: HKLM\Software\Microsoft\VisualStudio\\*\<versione >* \UserSettings\\`<CSPName>`, dove `<CSPName>` è il nome del punto di impostazioni personalizzato supporta il pacchetto VSPackage e  *\<versione >* è la versione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ad esempio 8.0.

> [!NOTE]
>  Il percorso radice di HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<versione >* può essere sostituito con un'alternativa radice quando il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è ambiente di sviluppo integrato (IDE) inizializzato. Per altre informazioni, vedere [opzioni della riga di comando](../../extensibility/command-line-switches-visual-studio-sdk.md).

 La struttura della voce del Registro di sistema è illustrata di seguito:

 HKLM\Software\Microsoft\VisualStudio\\*\<versione >* \UserSettings\

 `<CSPName`> = '#12345' s

 Pacchetto = '{XXXX XXXXXX XXXX XXXX XXXXXXXXX}'

 Categoria = '{YYYY YYYYYY aaaa aaaa YYYYYYYYY}'

 ResourcePackage = '{ZZZZ ZZZZZZ ZZZZ ZZZZ ZZZZZZZZZ}'

 AlternateParent = CategoryName

| Nome | Tipo | Dati | Descrizione |
|-----------------|--------| - | - |
| (Predefinito) | REG_SZ | Nome del punto di impostazioni personalizzato | Il nome della chiave, `<CSPName`>, è il nome non localizzato del punto di impostazioni personalizzato.<br /><br /> Per le implementazioni di base di MPF, il nome della chiave viene ottenuto combinando le `categoryName` e `objectName` gli argomenti delle <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> costruttore in `categoryName_objectName`.<br /><br /> La chiave può essere vuota o può contenere l'ID di riferimento per la stringa localizzata in una DLL satellite. Questo valore viene ottenuto dal `objectNameResourceID` argomento per il <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> costruttore. |
| Pacchetto | REG_SZ | GUID | Il GUID del pacchetto VSPackage che implementa il punto di impostazioni personalizzato.<br /><br /> Implementazioni basate su MPF usando il <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe, usare il costruttore `objectType` argomento che contiene il pacchetto VSPackage <xref:System.Type> e reflection per ottenere questo valore. |
| Category | REG_SZ | GUID | GUID che identifica la categoria di impostazioni.<br /><br /> Per le implementazioni di base degli assembly di interoperabilità, questo valore può essere un arbitrariamente scelto GUID, che il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE passa al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> metodi. Tutte le implementazioni di questi due metodi è necessario verificare i relativi argomenti di GUID.<br /><br /> Per le implementazioni di base di MPF questo GUID è ottenuto il <xref:System.Type> della classe che implementa il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] meccanismo delle impostazioni. |
| ResourcePackage | REG_SZ | GUID | Facoltativo.<br /><br /> Percorso che contiene DLL satellite nelle varie stringhe localizzate se non fornisce l'implementazione di VSPackage.<br /><br /> MPF Usa la reflection per ottenere la risorsa corretta VSPackage, pertanto il <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> classe non viene impostato questo argomento. |
| AlternateParent | REG_SZ | Nome della cartella sotto la pagina di opzioni degli strumenti che contiene il punto di impostazioni personalizzato. | Facoltativo.<br /><br /> È necessario impostare questo valore solo se un'implementazione di impostazioni supporta **opzioni del menu Strumenti** pagine che utilizzano il meccanismo di persistenza di [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] anziché il meccanismo nel modello di automazione per salvare lo stato.<br /><br /> In questi casi, il valore della chiave AlternateParent è il `topic` sezione il `topic.sub-topic` stringa utilizzata per identificare la particolare **ToolsOptions che dei** pagina. Ad esempio, per il **ToolsOptions che dei** pagina `"TextEditor.Basic"` il valore di AlternateParent sarebbe `"TextEditor"`.<br /><br /> Quando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> genera il punto di impostazioni personalizzato, è identico al nome di categoria. |
