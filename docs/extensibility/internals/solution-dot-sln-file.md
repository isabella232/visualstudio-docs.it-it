---
title: Soluzione (. Sln) file
description: Informazioni sul file con estensione sln, uno dei file che gestisce le informazioni sullo stato per un progetto in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9a8b857905a4e0a599584d6eecc03879b7e656081772071885bd25461b2220bd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121432202"
---
# <a name="solution-sln-file"></a>File di soluzione (con estensione sln)

Una soluzione è una struttura per organizzare i progetti in Visual Studio. La soluzione gestisce le informazioni sullo stato per i progetti in due file:

- File con estensione sln (basato su testo, condiviso)

- File con estensione suo (opzioni di soluzione binarie specifiche dell'utente)

Per altre informazioni sui file con estensione suo, vedere [Opzioni utente della soluzione (. Suo) File](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Se il pacchetto VSPackage viene caricato come risultato di un riferimento nel file con estensione sln, l'ambiente chiama per leggere <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> nel file con estensione sln.

Il file con estensione sln contiene informazioni basate su testo che l'ambiente usa per trovare e caricare i parametri nome-valore per i dati persistenti e i PACCHETTI VSPackage del progetto a cui fa riferimento. Quando un utente apre una soluzione, l'ambiente scorre le informazioni , e nel file con estensione sln per caricare la soluzione, i progetti all'interno della soluzione ed eventuali informazioni persistenti associate alla `preSolution` `Project` `postSolution` soluzione.

Il file di ogni progetto contiene informazioni aggiuntive lette dall'ambiente per popolare la gerarchia con gli elementi del progetto. La persistenza dei dati della gerarchia è controllata dal progetto. I dati in genere non vengono archiviati nel file con estensione sln, anche se è possibile scrivere intenzionalmente le informazioni sul progetto nel file con estensione sln, se si sceglie di farlo. Per altre informazioni sulla persistenza, vedere [Project Persistence](../../extensibility/internals/project-persistence.md) e Opening and Saving [Project Items](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Intestazione del file

L'intestazione di un file con estensione sln è simile alla seguente:

::: moniker range="vs-2017"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio 15
VisualStudioVersion = 15.0.26730.15
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definizioni

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Intestazione standard che definisce la versione del formato di file.

`# Visual Studio 15`\
La versione principale di Visual Studio ha salvato (più di recente) il file della soluzione. Queste informazioni controllano il numero di versione nell'icona della soluzione.

`VisualStudioVersion = 15.0.26730.15`\
La versione completa di Visual Studio il file della soluzione è stato salvato (più di recente). Se il file della soluzione viene salvato da una versione più recente di Visual Studio con la stessa versione principale, questo valore non viene aggiornato in modo da ridurre la varianza nei file della soluzione.

`MinimumVisualStudioVersion = 10.0.40219.1`\
La versione minima (meno recente) di Visual Studio in grado di aprire questo file di soluzione.

::: moniker-end

::: moniker range=">=vs-2019"

```
Microsoft Visual Studio Solution File, Format Version 12.00
# Visual Studio Version 16
VisualStudioVersion = 16.0.28701.123
MinimumVisualStudioVersion = 10.0.40219.1
```

### <a name="definitions"></a>Definizioni

`Microsoft Visual Studio Solution File, Format Version 12.00`\
Intestazione standard che definisce la versione del formato di file.

`# Visual Studio Version 16`\
La versione principale di Visual Studio ha salvato (più di recente) il file della soluzione. Queste informazioni controllano il numero di versione nell'icona della soluzione.

`VisualStudioVersion = 16.0.28701.123`\
La versione completa di Visual Studio il file della soluzione è stato salvato (più di recente). Se il file della soluzione viene salvato da una versione più recente di Visual Studio con la stessa versione principale, questo valore non viene aggiornato in modo da ridurre la varianza nel file.

`MinimumVisualStudioVersion = 10.0.40219.1`\
La versione minima (meno recente) di Visual Studio in grado di aprire questo file di soluzione.

::: moniker-end

## <a name="file-body"></a>Corpo del file

Il corpo di un file con estensione sln è costituito da diverse sezioni con etichetta `GlobalSection` , come nell'esempio seguente:

```
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
EndProject
Global
  GlobalSection(SolutionNotes) = postSolution
  EndGlobalSection
  GlobalSection(SolutionConfiguration) = preSolution
       ConfigName.0 = Debug
       ConfigName.1 = Release
  EndGlobalSection
  GlobalSection(ProjectDependencies) = postSolution
  EndGlobalSection
  GlobalSection(ProjectConfiguration) = postSolution
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86
  EndGlobalSection
  GlobalSection(ExtensibilityGlobals) = postSolution
  EndGlobalSection
  GlobalSection(ExtensibilityAddIns) = postSolution
  EndGlobalSection
EndGlobal
```

Per caricare una soluzione, l'ambiente esegue la sequenza di attività seguente:

1. L'ambiente legge la sezione Globale del file con estensione sln ed elabora tutte le sezioni contrassegnate come `preSolution` . In questo file di esempio è presente un'istruzione di questo tipo:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Quando l'ambiente legge il `GlobalSection('name')` tag, esegue il mapping del nome a un VSPackage usando il Registro di sistema. Il nome della chiave deve esistere nel Registro di sistema in [HKLM \\<Application ID Registry Root \> \SolutionPersistence\AggregateGUIDs]. Il valore predefinito delle chiavi è il GUID del pacchetto (REG_SZ) del VSPackage che ha scritto le voci.

2. L'ambiente carica il pacchetto VSPackage, chiama il VSPackage per l'interfaccia e chiama il metodo con i dati nella sezione in modo che il pacchetto VSPackage possa `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> archiviare i dati. L'ambiente ripete questo processo per ogni `preSolution` sezione.

3. L'ambiente scorre i blocchi di persistenza del progetto. In questo caso, è presente un progetto.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Questa istruzione contiene il GUID univoco del progetto e il GUID del tipo di progetto. Queste informazioni vengono usate dall'ambiente per trovare il file o i file di progetto appartenenti alla soluzione e il VSPackage necessario per ogni progetto. Il GUID del progetto viene passato a per caricare il pacchetto VSPackage specifico correlato al progetto, quindi il progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> viene caricato dal pacchetto VSPackage. In questo caso, il VSPackage caricato per questo progetto viene Visual Basic.

   Ogni progetto può rendere persistente un ID istanza di progetto univoco in modo che sia accessibile in base alle esigenze di altri progetti nella soluzione. Idealmente, se la soluzione e i progetti sono sotto il controllo del codice sorgente, il percorso del progetto deve essere relativo al percorso della soluzione. Quando la soluzione viene caricata per la prima volta, i file di progetto non possono essere nel computer dell'utente. Se il file di progetto viene archiviato nel server rispetto al file della soluzione, è relativamente semplice trovare e copiare il file di progetto nel computer dell'utente. Copia e carica quindi il resto dei file necessari per il progetto.

4. In base alle informazioni contenute nella sezione project del file con estensione sln, l'ambiente carica ogni file di progetto. Il progetto stesso è quindi responsabile del popolamento della gerarchia del progetto e del caricamento di eventuali progetti annidati.

5. Dopo l'elaborazione di tutte le sezioni del file con estensione sln, la soluzione viene visualizzata in Esplora soluzioni ed è pronta per la modifica da parte dell'utente.

Se un VSPackage che implementa un progetto nella soluzione non viene caricato, viene chiamato il metodo e ogni altro progetto nella soluzione ha la possibilità di ignorare le modifiche apportate durante <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> il caricamento. Se si verificano errori di analisi, il maggior numero possibile di informazioni viene mantenuto con i file della soluzione e l'ambiente visualizza una finestra di dialogo che avvisa l'utente che la soluzione è danneggiata.

Quando la soluzione viene salvata o chiusa, il metodo viene chiamato e passato alla gerarchia per verificare se sono state apportate modifiche alla soluzione che devono essere immesse nel file con estensione <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> sln. Un valore Null, passato a in , indica che le `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> informazioni vengono rese persistenti per la soluzione. Se il valore non è Null, le informazioni persistenti sono relative a un progetto specifico, determinato dal puntatore <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> all'interfaccia .

Se sono presenti informazioni da salvare, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> l'interfaccia viene chiamata con un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> metodo . Il metodo viene quindi chiamato dall'ambiente per recuperare le coppie nome-valore dall'interfaccia e scrivere le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> informazioni nel file con estensione `IPropertyBag` sln.

`SaveSolutionProps` Gli oggetti e vengono chiamati in modo ricorsivo dall'ambiente per recuperare le informazioni da salvare dall'interfaccia fino a quando tutte le modifiche non sono state immesse `WriteSolutionProps` nel file con estensione `IPropertyBag` sln. In questo modo, è possibile assicurare che le informazioni verranno rese persistenti con la soluzione e disponibili alla successiva apertura della soluzione.

Ogni PACCHETTO VSPackage caricato viene enumerato per verificare se contiene elementi da salvare nel file con estensione sln. È solo in fase di caricamento che viene eseguita una query delle chiavi del Registro di sistema. L'ambiente è a conoscenza di tutti i pacchetti caricati perché sono in memoria al momento del salvataggio della soluzione.

Solo il file con estensione sln contiene voci nelle `preSolution` sezioni `postSolution` e . Non sono presenti sezioni simili nel file con estensione suo perché la soluzione necessita di queste informazioni per il corretto caricamento. Il file con estensione suo contiene opzioni specifiche dell'utente, ad esempio note private, che non devono essere condivise o inserite nel controllo del codice sorgente.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [File delle opzioni utente della soluzione (con estensione suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Soluzioni](../../extensibility/internals/solutions-overview.md)
