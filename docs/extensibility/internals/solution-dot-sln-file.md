---
title: Soluzione (. Sln) file
description: Informazioni sul file sln, uno dei file che gestisce le informazioni sullo stato per un progetto in Visual Studio.
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
ms.openlocfilehash: 5c036504bd5a7b881edab2d2bf4ef373706d65f9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062745"
---
# <a name="solution-sln-file"></a>File di soluzione (sln)

Una soluzione è una struttura per organizzare i progetti in Visual Studio. La soluzione mantiene le informazioni sullo stato per i progetti in due file:

- File con estensione sln (basato su testo, condiviso)

- File con estensione suo (opzioni di soluzione binarie specifiche dell'utente)

Per altre informazioni sui file con estensione suo, vedere [Opzioni utente della soluzione (. Suo) File](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Se il pacchetto VSPackage viene caricato come risultato del riferimento nel file sln, l'ambiente chiama per leggere nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> file sln.

Il file sln contiene informazioni basate su testo utilizzate dall'ambiente per trovare e caricare i parametri nome-valore per i dati persistenti e i pacchetti VSPackage del progetto a cui fa riferimento. Quando un utente apre una soluzione, l'ambiente scorre le informazioni , e nel file sln per caricare la soluzione, i progetti all'interno della soluzione e tutte le informazioni persistenti associate `preSolution` `Project` alla `postSolution` soluzione.

Il file di ogni progetto contiene informazioni aggiuntive lette dall'ambiente per popolare la gerarchia con gli elementi del progetto. La persistenza dei dati della gerarchia è controllata dal progetto. I dati non vengono in genere archiviati nel file sln, anche se è possibile scrivere intenzionalmente informazioni sul progetto nel file sln se si sceglie di eseguire questa operazione. Per altre informazioni sulla persistenza, vedere [Project persistenza](../../extensibility/internals/project-persistence.md) e [apertura e salvataggio](../../extensibility/internals/opening-and-saving-project-items.md)Project elementi .

## <a name="file-header"></a>Intestazione del file

L'intestazione di un file sln è simile alla seguente:

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
La versione principale di Visual Studio che (più di recente) ha salvato questo file di soluzione. Queste informazioni controllano il numero di versione nell'icona della soluzione.

`VisualStudioVersion = 15.0.26730.15`\
La versione completa di Visual Studio che (più di recente) ha salvato il file della soluzione. Se il file della soluzione viene salvato da una versione più recente di Visual Studio con la stessa versione principale, questo valore non viene aggiornato in modo da ridurre la varianza nei file della soluzione.

`MinimumVisualStudioVersion = 10.0.40219.1`\
La versione minima (meno recente) Visual Studio possibile aprire questo file di soluzione.

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
La versione principale di Visual Studio che (più di recente) ha salvato questo file di soluzione. Queste informazioni controllano il numero di versione nell'icona della soluzione.

`VisualStudioVersion = 16.0.28701.123`\
La versione completa di Visual Studio che (più di recente) ha salvato il file della soluzione. Se il file di soluzione viene salvato da una versione più recente di Visual Studio con la stessa versione principale, questo valore non viene aggiornato in modo da ridurre la varianza nel file.

`MinimumVisualStudioVersion = 10.0.40219.1`\
La versione minima (meno recente) Visual Studio possibile aprire questo file di soluzione.

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

1. L'ambiente legge la sezione Globale del file sln ed elabora tutte le sezioni contrassegnate con `preSolution` . In questo file di esempio è presente un'istruzione di questo tipo:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Quando l'ambiente legge il `GlobalSection('name')` tag, esegue il mapping del nome a un VSPackage usando il Registro di sistema. Il nome della chiave deve esistere nel Registro di sistema in [HKLM \\<application ID Registry Root \> \SolutionPersistence\AggregateGUIDs]. Il valore predefinito delle chiavi è il GUID del pacchetto (REG_SZ) del pacchetto VSPackage che ha scritto le voci.

2. L'ambiente carica il pacchetto VSPackage, chiama il pacchetto VSPackage per l'interfaccia e chiama il metodo con i dati nella sezione in modo che il pacchetto VSPackage possa `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> archiviare i dati. L'ambiente ripete questo processo per ogni `preSolution` sezione.

3. L'ambiente scorre i blocchi di persistenza del progetto. In questo caso, è presente un progetto.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Questa istruzione contiene il GUID univoco del progetto e il GUID del tipo di progetto. Queste informazioni vengono usate dall'ambiente per trovare il file di progetto o i file appartenenti alla soluzione e il pacchetto VSPackage necessario per ogni progetto. Il GUID del progetto viene passato a per caricare il pacchetto VSPackage specifico correlato al progetto, quindi il progetto viene <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> caricato dal pacchetto VSPackage. In questo caso, il pacchetto VSPackage caricato per questo progetto viene Visual Basic.

   Ogni progetto può rendere persistente un ID istanza di progetto univoco in modo che sia accessibile in base alle esigenze di altri progetti nella soluzione. Idealmente, se la soluzione e i progetti sono sotto controllo del codice sorgente, il percorso del progetto deve essere relativo al percorso della soluzione. Quando la soluzione viene caricata per la prima volta, i file di progetto non possono essere nel computer dell'utente. Se il file di progetto viene archiviato nel server rispetto al file della soluzione, è relativamente semplice trovare e copiare il file di progetto nel computer dell'utente. Copia quindi e carica gli altri file necessari per il progetto.

4. In base alle informazioni contenute nella sezione project del file sln, l'ambiente carica ogni file di progetto. Il progetto stesso è quindi responsabile del popolamento della gerarchia del progetto e del caricamento di eventuali progetti annidati.

5. Dopo l'elaborazione di tutte le sezioni del file sln, la soluzione viene visualizzata in Esplora soluzioni ed è pronta per la modifica da parte dell'utente.

Se un VSPackage che implementa un progetto nella soluzione non viene caricato, viene chiamato il metodo e a ogni altro progetto nella soluzione viene data la possibilità di ignorare le modifiche che potrebbe essere stato apportato durante <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> il caricamento. Se si verificano errori di analisi, il maggior numero possibile di informazioni viene mantenuto con i file della soluzione e l'ambiente visualizza una finestra di dialogo che avvisa l'utente che la soluzione è danneggiata.

Quando la soluzione viene salvata o chiusa, il metodo viene chiamato e passato alla gerarchia per verificare se sono state apportate modifiche alla soluzione che devono essere immesse nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> file sln. Un valore Null, passato a in , indica che le `QuerySaveSolutionProps` <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> informazioni vengono rese persistenti per la soluzione. Se il valore non è Null, le informazioni persistenti sono relative a un progetto specifico, determinato dal puntatore <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> all'interfaccia .

Se sono presenti informazioni da salvare, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> l'interfaccia viene chiamata con un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> metodo . Il metodo viene quindi chiamato dall'ambiente per recuperare le coppie nome-valore dall'interfaccia e scrivere le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> `IPropertyBag` informazioni nel file sln.

`SaveSolutionProps` Gli oggetti e vengono chiamati in modo ricorsivo dall'ambiente per recuperare le informazioni da salvare dall'interfaccia fino a quando tutte le modifiche non sono state immesse `WriteSolutionProps` `IPropertyBag` nel file sln. In questo modo, è possibile assicurare che le informazioni verranno rese persistenti con la soluzione e saranno disponibili alla successiva apertura della soluzione.

Ogni VSPackage caricato viene enumerato per verificare se ha qualcosa da salvare nel file con estensione sln. È solo in fase di caricamento che viene eseguita la query delle chiavi del Registro di sistema. L'ambiente è a conoscenza di tutti i pacchetti caricati perché sono in memoria al momento del salvataggio della soluzione.

Solo il file sln contiene voci nelle `preSolution` sezioni e `postSolution` . Non sono presenti sezioni simili nel file con estensione suo perché la soluzione richiede che queste informazioni siano caricate correttamente. Il file suo contiene opzioni specifiche dell'utente, ad esempio note private, che non devono essere condivise o inserite nel controllo del codice sorgente.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [File delle opzioni utente della soluzione (con estensione suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Soluzioni](../../extensibility/internals/solutions-overview.md)
