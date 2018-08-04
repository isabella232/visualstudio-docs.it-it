---
title: Creazione di pagine delle opzioni | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 834edb926142637a250cf4a695d5d1d54e103977
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499478"
---
# <a name="create-options-pages"></a>Creazione di pagine Opzioni
Nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] framework di pacchetto gestito, le classi derivate da <xref:Microsoft.VisualStudio.Shell.DialogPage> estendere il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE aggiungendo **opzioni** pagine sotto il **strumenti** menu.  
  
 Oggetto che implementa una determinata **scelta degli strumenti** pagina è associata a pacchetti VSPackage specifici dal <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> oggetto.  
  
 Poiché l'ambiente di un'istanza dell'oggetto che implementa un particolare **opzioni del menu Strumenti** pagina quando tale particolare pagina viene visualizzato dall'IDE:  
  
-   Oggetto **scelta degli strumenti** pagina deve essere implementata nel proprio oggetto e non per l'oggetto che implementa un pacchetto VSPackage.  
  
-   Un oggetto non può implementare più **opzioni del menu Strumenti** pagine.  
  
## <a name="register-as-a-tools-options-page-provider"></a>Registrare un provider di pagina di opzioni del menu Strumenti  
 Una configurazione dell'utente supporta VSPackage attraverso **opzioni degli strumenti** pagine indica gli oggetti che li fornisce **opzioni degli strumenti** pagine applicando le istanze di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> applicato per i <xref:Microsoft.VisualStudio.Shell.Package>implementazione.  
  
 Deve esistere un'istanza di <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> per ogni <xref:Microsoft.VisualStudio.Shell.DialogPage>-derivato tipo che implementa un **ToolsOptions** pagina.  
  
 Ogni istanza del <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> utilizza il tipo che implementa le **opzioni degli strumenti** pagina, le stringhe che contengono la categoria e sottocategoria utilizzato per identificare una **opzioni del menu Strumenti** pagina e delle risorse informazioni per registrare il tipo come provider di un **opzioni del menu Strumenti** pagina.  
  
## <a name="persist-tools-options-page-state"></a>Rendere persistente lo stato della pagina di opzioni del menu Strumenti  
 Se un **ToolsOptions** implementazione della pagina viene registrato con il supporto di automazione abilitato, l'IDE mantiene lo stato della pagina insieme a tutti gli altri **opzioni del menu Strumenti** pagine.  
  
 Un pacchetto VSPackage può gestire il proprio persistenza usando <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>. Solo uno o l'altro metodo di persistenza deve essere utilizzato.  
  
## <a name="implement-dialogpage-class"></a>Implementare una classe DialogPage  
 Oggetto che fornisce un'implementazione di VSPackage un <xref:Microsoft.VisualStudio.Shell.DialogPage>-tipo derivato possa sfruttare i vantaggi delle funzionalità ereditato seguenti:  
  
-   Una finestra dell'interfaccia utente predefinita.  
  
-   Oggetto predefinito disponibile il meccanismo di persistenza se <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> viene applicato alla classe, o se il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A> è impostata su `true` per il <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> applicato alla classe.  
  
-   Supporto di automazione.  
  
 Il requisito minimo per un oggetto che implementa una **ToolsOptions** pagina usando <xref:Microsoft.VisualStudio.Shell.DialogPage> consiste nell'aggiunta di proprietà pubbliche.  
  
 Se la classe registrata correttamente come un **opzioni del menu Strumenti** sue proprietà pubbliche sono disponibili nella pagina provider, il **opzioni** sezione del **strumenti** menu sotto forma di un griglia delle proprietà.  
  
 Tutte le funzionalità predefinite di questi può essere sottoposto a override. Ad esempio, per creare un utente più sofisticato interfaccia richiede l'override solo l'implementazione predefinita di <xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>.  
  
## <a name="example"></a>Esempio  
 Ciò che segue è un'implementazione semplice "Hello world" di una pagina di opzioni. Aggiungendo il codice seguente a un progetto predefinito creato dal modello di pacchetto di Visual Studio con il **comando di Menu** selezionata l'opzione illustrerà in modo adeguato funzionalità relative alle pagine di opzione.  
  
### <a name="description"></a>Descrizione  
 La classe seguente definisce una pagina di opzioni minimo "Hello world". All'apertura, l'utente può impostare pubblico `HelloWorld` proprietà in una griglia delle proprietà.  
  
### <a name="code"></a>Codice  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>Descrizione  
 Applicando l'attributo seguente alla classe dei package rende disponibili le opzioni di pagina quando viene caricato il pacchetto. I numeri sono arbitrari ID di risorsa per la categoria e la pagina e il valore booleano alla fine specifica se la pagina supporta l'automazione.  
  
### <a name="code"></a>Codice  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>Descrizione  
 Il gestore eventi seguente visualizza un risultato in base al valore della proprietà impostata nella pagina delle opzioni. Usa il <xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A> metodo con il risultato in modo esplicito il cast nel tipo di pagina di opzioni personalizzate per le proprietà esposte dalla pagina di accesso.  
  
 Nel caso di un progetto generato dal modello di pacchetto, chiamare questa funzione dal `MenuItemCallback` aggiunta funzione aggiungerlo al comando predefinito per il **strumenti** menu.  
  
### <a name="code"></a>Codice  
 [!code-csharp[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs)]
 [!code-vb[UI_UserSettings_ToolsOptionPages#08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere le opzioni e impostazioni utente](../../extensibility/extending-user-settings-and-options.md)   
 [Supporto di automazione per le pagine di opzioni](../../extensibility/internals/automation-support-for-options-pages.md)