---
title: Creazione di istanze di progetto tramite le factory di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31ba5dd11af18f8a723b2271544eff2bd292e2e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709054"
---
# <a name="create-project-instances-by-using-project-factories"></a>Creare istanze di progetto utilizzando le factory di progettoCreate project instances by using project factories
I tipi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di progetto in usa una factory del *progetto* per creare istanze di oggetti di progetto. Una factory del progetto è simile a una class factory standard per gli oggetti COM cocreabili. Tuttavia, gli oggetti di progetto non sono cocreabili; possono essere creati solo utilizzando una fabbrica di progetto.

 L'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiama la factory del progetto implementata nel pacchetto VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]quando un utente carica un progetto esistente o crea un nuovo progetto in . Il nuovo oggetto di progetto fornisce all'IDE informazioni sufficienti per popolare **Esplora soluzioni**. Il nuovo oggetto di progetto fornisce anche le interfacce necessarie per supportare tutte le azioni dell'interfaccia utente pertinenti avviate dall'IDE.

 È possibile <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> implementare l'interfaccia in una classe nel progetto. In genere, risiede nel proprio modulo.

 I progetti che supportano l'aggregazione da un proprietario devono mantenere una chiave del proprietario nel file di progetto. Quando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> il metodo viene chiamato su un progetto con una chiave del proprietario, il `CreateProject` progetto di proprietà converte la chiave del proprietario in un GUID di factory del progetto, quindi chiama il metodo su questa factory del progetto per eseguire la creazione effettiva.

## <a name="create-an-owned-project"></a>Creare un progetto di proprietà
 Un proprietario crea un progetto di proprietà in due fasi:An owner creates an owned project in two phases:

1. Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metodo . In questo modo il progetto di proprietà ha la possibilità `IUnknown`di creare un oggetto progetto aggregato in base all'input che controlla . Il progetto di `IUnknown` proprietà passa l'oggetto interno e l'oggetto aggregato al progetto proprietario. Questo dà al progetto di proprietà `IUnknown`la possibilità di memorizzare l'interno .

2. Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metodo . Il progetto di proprietà esegue tutte le relative istanze quando viene chiamato questo metodo anziché chiamare `IVsProjectFactory::CreateProject` come sarebbe il caso per i progetti che non sono di proprietà. L'enumerazione di input `VSOWNEDPROJECTOBJECT` è in genere il progetto di proprietà aggregato. Il progetto di proprietà può utilizzare questa variabile per determinare se il relativo oggetto di progetto è già stato creato (cookie non è uguale a NULL) o deve essere creato (cookie è uguale a NULL).

   I tipi di progetto sono identificati da un GUID di progetto univoco, simile al CLSID di un oggetto COM creabile. In genere, una factory del progetto gestisce la creazione di istanze di un singolo tipo di progetto, anche se è possibile fare in modo che una factory del progetto gestisca più guid del tipo di progetto.

   I tipi di progetto sono associati a una particolare estensione di file. Quando un utente tenta di aprire un file di progetto esistente o tenta di creare un nuovo progetto clonando un modello, l'IDE utilizza l'estensione sul file per determinare il GUID del progetto corrispondente.

   Non appena l'IDE determina se è necessario creare un nuovo progetto o aprire un progetto esistente di un determinato tipo, l'IDE utilizza le informazioni nel Registro di sistema in [HKEY_LOCAL_MACHINE , **Software MicrosoftVisualA) 8.0 Projects]** per individuare quale VSPackage implementa la factory di progetto necessaria. L'IDE carica questo VSPackage.The IDE loads this VSPackage. Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodo, il pacchetto VSPackage deve registrare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> factory del progetto con l'IDE chiamando il metodo .

   Il metodo principale `IVsProjectFactory` dell'interfaccia è <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, che deve gestire due scenari: l'apertura di un progetto esistente e la creazione di un nuovo progetto. La maggior parte dei progetti archivia lo stato del progetto in un file di progetto. In genere, i nuovi progetti vengono creati creando `CreateProject` una copia del file modello passato al metodo e quindi aprendo la copia. Viene creata un'istanza dei progetti esistenti `CreateProject` aprendo direttamente il file di progetto passato al metodo. Il `CreateProject` metodo può visualizzare funzionalità aggiuntive dell'interfaccia utente per l'utente in base alle esigenze.

   Un progetto può inoltre non utilizzare file e, invece, archiviare lo stato del progetto in un meccanismo di archiviazione diverso dal file system, ad esempio un database o un server Web. In questo caso, il parametro `CreateProject` del nome file passato al metodo non è in realtà un percorso del file system, ma una stringa univoca, ovvero un URL, per identificare i dati del progetto. Non è necessario copiare i file `CreateProject` di modello passati a per attivare la sequenza di costruzione appropriata da eseguire.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Elenco di controllo: creare nuovi tipi di progettoChecklist: Create new project types](../../extensibility/internals/checklist-creating-new-project-types.md)
