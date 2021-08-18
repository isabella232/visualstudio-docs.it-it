---
title: Creazione Project istanze usando Project factory | Microsoft Docs
description: Informazioni su come creare istanze della classe di progetto usando le factory di progetto nell Visual Studio ide (Integrated Development Environment).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1fc9fa9d4f10c59d4e17f2314cdbed80da26c3b5e24b115fb755c1fce9645b24
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448195"
---
# <a name="create-project-instances-by-using-project-factories"></a>Creare istanze del progetto usando le factory di progetto
Project tipi in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usano una *factory di progetto per* creare istanze di oggetti di progetto. Una factory di progetto è simile a una factory standard class factory per gli oggetti COM cocreabili. Tuttavia, gli oggetti di progetto non sono cocreabili. Possono essere creati solo usando una factory del progetto.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'IDE chiama la factory del progetto implementata nel VSPackage quando un utente carica un progetto esistente o crea un nuovo progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Il nuovo oggetto progetto fornisce all'IDE informazioni sufficienti per popolare **Esplora soluzioni**. Il nuovo oggetto progetto fornisce anche le interfacce necessarie per supportare tutte le azioni dell'interfaccia utente pertinenti avviate dall'IDE.

 È possibile implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> l'interfaccia in una classe nel progetto. In genere, si trova nel proprio modulo.

 I progetti che supportano l'aggregazione da parte di un proprietario devono rendere persistente una chiave del proprietario nel file di progetto. Quando il metodo viene chiamato su un progetto con una chiave di proprietario, il progetto di proprietà converte la chiave del proprietario in un GUID della factory del progetto e quindi chiama il metodo in questa factory del progetto per eseguire la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> `CreateProject` creazione effettiva.

## <a name="create-an-owned-project"></a>Creare un progetto di proprietà
 Un proprietario crea un progetto di proprietà in due fasi:

1. Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metodo . In questo modo il progetto di proprietà ha la possibilità di creare un oggetto di progetto aggregato basato sull'input che controlla `IUnknown` . Il progetto di proprietà passa di `IUnknown` nuovo l'oggetto interno e l'oggetto aggregato al progetto proprietario. In questo modo il progetto di proprietà ha la possibilità di archiviare l'oggetto `IUnknown` interno.

2. Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metodo . Il progetto di proprietà esegue tutte le relative istanze quando viene chiamato questo metodo anziché chiamare come nel caso di progetti che `IVsProjectFactory::CreateProject` non sono di proprietà. L'enumerazione di input `VSOWNEDPROJECTOBJECT` è in genere il progetto di proprietà aggregato. Il progetto di proprietà può usare questa variabile per determinare se il relativo oggetto di progetto è già stato creato (cookie diverso da NULL) o deve essere creato (cookie uguale a NULL).

   Project tipi sono identificati da un GUID di progetto univoco, simile al CLSID di un oggetto COM cocreabile. In genere, una factory del progetto gestisce la creazione di istanze di un singolo tipo di progetto, anche se è possibile che una factory del progetto gestisca più GUID di tipo di progetto.

   Project tipi di file sono associati a una determinata estensione di file. Quando un utente tenta di aprire un file di progetto esistente o tenta di creare un nuovo progetto clonando un modello, l'IDE usa l'estensione nel file per determinare il GUID del progetto corrispondente.

   Non appena l'IDE determina se deve creare un nuovo progetto o aprire un progetto esistente di un determinato tipo, l'IDE usa le informazioni nel Registro di sistema in **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** per trovare il pacchetto VSPackage che implementa la factory del progetto richiesta. L'IDE carica questo VSPackage. Nel metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> il vspackage deve registrare la factory del progetto con l'IDE chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> metodo .

   Il metodo principale dell'interfaccia è , che deve gestire due scenari: l'apertura `IVsProjectFactory` di un progetto esistente e la creazione di un nuovo <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> progetto. La maggior parte dei progetti archivia lo stato del progetto in un file di progetto. In genere, i nuovi progetti vengono creati effettuando una copia del file modello passato al `CreateProject` metodo e quindi aprendo la copia. Viene creata un'istanza dei progetti esistenti aprendo direttamente il file di progetto passato al `CreateProject` metodo . Il `CreateProject` metodo può visualizzare funzionalità aggiuntive dell'interfaccia utente all'utente in base alle esigenze.

   Un progetto può anche non usare file e, al contrario, archiviarne lo stato del progetto in un meccanismo di archiviazione diverso dal file system, ad esempio un database o un server Web. In questo caso, il parametro del nome file passato al metodo non è in realtà un percorso file system ma una stringa univoca, ovvero un URL, per identificare i dati `CreateProject` del progetto. Non è necessario copiare i file modello passati a per `CreateProject` attivare la sequenza di costruzione appropriata da eseguire.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Elenco di controllo: Creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
