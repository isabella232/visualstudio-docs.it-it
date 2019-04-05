---
title: Creazione di istanze del progetto tramite le factory di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b33d5d1a09425a18f0c9489b15147e3355e45c99
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965817"
---
# <a name="creating-project-instances-by-using-project-factories"></a>Creazione di istanze di progetto tramite le factory di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tipi di progetto in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usano un *factory progetto* per creare istanze di oggetti del progetto. È simile a una factory di classe standard per gli oggetti COM cocreatable una factory progetto. Oggetti del progetto non sono tuttavia cocreatable: possono essere creati solo mediante una factory progetto.  
  
 Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE chiama la factory del progetto implementata nel pacchetto VSPackage quando un utente carica un progetto esistente o crea un nuovo progetto in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Il nuovo oggetto di progetto fornisce l'IDE con le informazioni necessarie per popolare Esplora soluzioni. Il nuovo oggetto di progetto fornisce inoltre le interfacce necessarie per supportare tutte le azioni dell'interfaccia utente rilevante avviate dall'IDE.  
  
 È possibile implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaccia in una classe nel progetto. In genere, si trova in un proprio modulo.  
  
 Per un esempio di un'implementazione del `IVsProjectFactory` l'interfaccia, vedere PrjFac.cpp contenuta nel [progetto base](http://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) directory degli esempi.  
  
 I progetti che supportano l'aggregazione da un proprietario devono mantenere una chiave del proprietario nel relativo file di progetto. Quando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metodo viene chiamato su un progetto con una chiave del proprietario, il progetto di proprietà converte la chiave del proprietario in una factory progetto GUID chiama quindi il `CreateProject` metodo factory del progetto per eseguire la creazione effettiva.  
  
## <a name="creating-an-owned-project"></a>Creazione di un progetto di proprietà  
 Un proprietario crea un progetto di proprietà in due fasi:  
  
1. Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> (metodo). In questo modo il progetto di proprietà per creare un oggetto di progetto aggregato basato sull'input che controlla `IUnknown`. Il progetto di proprietà passa interna `IUnknown` e l'oggetto aggregato al progetto proprietario. In questo modo il progetto di proprietà per l'archiviazione interna `IUnknown`.  
  
2. Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> (metodo). Il progetto di proprietà non tutti la creazione dell'istanza quando viene chiamato questo metodo invece di chiamare `IVsProjectFactory::CreateProject` come invece accade per i progetti che non sono di proprietà. L'input `VSOWNEDPROJECTOBJECT` enumerazione viene in genere il progetto di proprietà aggregato. Il progetto di proprietà è possibile usare questa variabile per determinare se è già stato creato il relativo oggetto di progetto (cookie diverso da NULL) o deve essere creato (cookie uguale a NULL).  
  
   Tipi di progetto vengono identificati da un GUID, simile al CLSID di un oggetto COM cocreatable univoco del progetto. In genere, gli handle di factory di un progetto creazione di istanze di un singolo tipo di progetto, anche se è possibile disporre di una factory del progetto di gestire più di un tipo di progetto GUID.  
  
   Tipi di progetto sono associati a un'estensione particolare. Quando un utente tenta di aprire un file di progetto esistente o si tenta di creare un nuovo progetto tramite la clonazione di un modello, l'IDE Usa l'estensione per il file per determinare il GUID del progetto corrispondente.  
  
   Non appena l'IDE determina che se deve creare un nuovo progetto o aprire un progetto esistente di un determinato tipo, l'IDE Usa le informazioni nel Registro di sistema in [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] per individuare l'oggetto Pacchetto VSPackage implementa la factory di progetto necessari. L'IDE carica questo pacchetto VSPackage. Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodo, il pacchetto VSPackage deve registrare la factory del progetto con l'IDE chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> (metodo).  
  
   Il metodo principale del `IVsProjectFactory` interfaccia è <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> che devono gestire due scenari: apertura di un progetto esistente e crea un nuovo progetto. La maggior parte dei progetti archiviano il proprio stato di progetto in un file di progetto. In genere, i nuovi progetti vengono creati tramite una copia del file del modello passata al `CreateProject` (metodo) e quindi aprendo la copia. I progetti esistenti vengono create istanze tramite direttamente l'apertura del file di progetto passato a `CreateProject` (metodo). Il `CreateProject` metodo consente di visualizzare le funzionalità dell'interfaccia utente aggiuntive all'utente in base alle esigenze.  
  
   Un progetto può anche non usare alcun file e, invece di archiviare lo stato di progetto in un meccanismo di archiviazione diverso dal file system, ad esempio un database o un server Web. In questo caso, il parametro del nome file passato al `CreateProject` metodo non è effettivamente un percorso del file system, ma una stringa univoca, ovvero un URL, per identificare i dati del progetto. Non è necessaria copiare i file di modello che vengono passati al `CreateProject` per attivare la sequenza di costruzione appropriate da eseguire.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
