---
title: Soluzione (. Sln) file
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f4eee1f0a5e8371d239b3c33d10e1d9d7998095
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705323"
---
# <a name="solution-sln-file"></a>File di soluzione (sln)

A solution is a structure for organizing projects in Visual Studio. La soluzione gestisce le informazioni sullo stato per i progetti in due file:The solution maintains the state information for projects in two files:

- File sln (basato su testo, condiviso)

- File .suo (opzioni della soluzione binarie e specifiche dell'utente)

Per altre informazioni sui file con estensione suo, vedere [Opzioni utente soluzione (. Suo) File](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Se il pacchetto VSPackage viene caricato come risultato di riferimento nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> file sln, l'ambiente chiama per leggere il file sln.

Il file sln contiene informazioni basate su testo che l'ambiente utilizza per trovare e caricare i parametri nome-valore per i dati persistenti e il progetto VSPackage a cui fa riferimento. Quando un utente apre una soluzione, `preSolution` `Project`l'ambiente scorre le informazioni , e nel `postSolution` file sln per caricare la soluzione, i progetti all'interno della soluzione e tutte le informazioni persistenti associate alla soluzione.

Ogni file del progetto contiene informazioni aggiuntive lette dall'ambiente per popolare la gerarchia con gli elementi del progetto. La persistenza dei dati della gerarchia è controllata dal progetto. I dati non vengono normalmente memorizzati nel file sln, anche se è possibile scrivere intenzionalmente le informazioni sul progetto nel file SLN se si sceglie di farlo. Per ulteriori informazioni sulla persistenza, vedere [Persistenza del progetto](../../extensibility/internals/project-persistence.md) e [apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Intestazione file

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
La versione completa di Visual Studio che (più di recente) ha salvato il file di soluzione. Se il file di soluzione viene salvato da una versione più recente di Visual Studio con la stessa versione principale, questo valore non viene aggiornato in modo da ridurre la varianza nei file di soluzione.

`MinimumVisualStudioVersion = 10.0.40219.1`\
La versione minima (meno recente) di Visual Studio che può aprire questo file di soluzione.

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
La versione completa di Visual Studio che (più di recente) ha salvato il file di soluzione. Se il file di soluzione viene salvato da una versione più recente di Visual Studio con la stessa versione principale, questo valore non viene aggiornato in modo da ridurre la varianza nel file.

`MinimumVisualStudioVersion = 10.0.40219.1`\
La versione minima (meno recente) di Visual Studio che può aprire questo file di soluzione.

::: moniker-end

## <a name="file-body"></a>Corpo del file

Il corpo di un file .sln `GlobalSection`è costituito da diverse sezioni etichettate, in questo modo:

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

Per caricare una soluzione, l'ambiente esegue la sequenza di attività seguente:To load a solution, the environment performs the following sequence of tasks:

1. L'ambiente legge la sezione Globale del file .sln `preSolution`ed elabora tutte le sezioni contrassegnate con . In questo file di esempio, esiste un'istruzione di questo tipo:In this example file, there is one such statement:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Quando l'ambiente `GlobalSection('name')` legge il tag, esegue il mapping del nome a un VSPackage utilizzando il Registro di sistema. Il nome della chiave deve essere\\ presente nel Registro di sistema in [HKLM<radice\>del Registro di sistema dell'ID applicazione, ovvero SolutionPersistence, AggregateGUIDs]. Il valore predefinito delle chiavi è il GUID del pacchetto (REG_SZ) del pacchetto VSPackage che ha scritto le voci.

2. L'ambiente carica il `QueryInterface` pacchetto VSPackage, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> le chiamate sul <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> pacchetto VSPackage per l'interfaccia e chiama il metodo con i dati nella sezione in modo che il pacchetto VSPackage può archiviare i dati. L'ambiente ripete questo `preSolution` processo per ogni sezione.

3. L'ambiente scorre i blocchi di persistenza del progetto. In questo caso, c'è un progetto.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Questa istruzione contiene il GUID univoco del progetto e il GUID del tipo di progetto. Queste informazioni vengono utilizzate dall'ambiente per trovare il file di progetto o i file appartenenti alla soluzione e il pacchetto VSPackage necessario per ogni progetto. Il GUID del <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> progetto viene passato per caricare il pacchetto VSPackage specifico correlato al progetto, quindi il progetto viene caricato dal pacchetto VSPackage. In this case, the VSPackage that is loaded for this project is Visual Basic.

   Ogni progetto può rendere persistente un ID istanza di progetto univoco in modo che sia possibile accedervi in base alle esigenze di altri progetti nella soluzione. In teoria, se la soluzione e i progetti sono sotto il controllo del codice sorgente, il percorso del progetto deve essere relativo al percorso della soluzione. Quando la soluzione viene caricata per la prima volta, i file di progetto non possono trovarsi nel computer dell'utente. Avendo il file di progetto archiviato sul server rispetto al file di soluzione, è relativamente semplice per il file di progetto da trovare e copiare nel computer dell'utente. Quindi copia e carica il resto dei file necessari per il progetto.

4. In base alle informazioni contenute nella sezione del progetto del file sln, l'ambiente carica ogni file di progetto. Il progetto stesso è quindi responsabile del popolamento della gerarchia del progetto e del caricamento di tutti i progetti annidati.

5. Dopo l'elaborazione di tutte le sezioni del file sln, la soluzione viene visualizzata in Esplora soluzioni ed è pronta per la modifica da parte dell'utente.

Se un pacchetto VSPackage che implementa un progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> nella soluzione non riesce a caricare, il metodo viene chiamato e ogni altro progetto nella soluzione viene data la possibilità di ignorare le modifiche che potrebbe aver apportato durante il caricamento. Se si verificano errori di analisi, il maggior numero possibile di informazioni viene mantenuto con i file della soluzione e l'ambiente visualizza una finestra di dialogo che avvisa l'utente che la soluzione è danneggiata.

Quando la soluzione viene salvata <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> o chiusa, il metodo viene chiamato e passato alla gerarchia per verificare se sono state apportate modifiche alla soluzione che devono essere immesse nel file sln. Un valore null, `QuerySaveSolutionProps` passato <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>a in , indica che le informazioni vengono mantenute per la soluzione. Se il valore non è null, le informazioni persistenti sono per <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> un progetto specifico, determinato dal puntatore all'interfaccia.

Se sono presenti informazioni da <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> salvare, l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> viene chiamata con un puntatore al metodo . Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> metodo viene quindi chiamato dall'ambiente per `IPropertyBag` recuperare le coppie nome-valore dall'interfaccia e scrivere le informazioni nel file sln.

`SaveSolutionProps`e `WriteSolutionProps` gli oggetti vengono chiamati in modo ricorsivo dall'ambiente per recuperare le informazioni da salvare dall'interfaccia `IPropertyBag` fino a quando tutte le modifiche sono state immesse nel file sln. In questo modo, è possibile assicurarsi che le informazioni verranno mantenute con la soluzione e disponibili alla successiva apertura della soluzione.

Ogni VSPackage caricato viene enumerato per vedere se ha qualcosa da salvare in file Sln. È solo in fase di caricamento che viene eseguita una query sulle chiavi del Registro di sistema. L'ambiente conosce tutti i pacchetti caricati perché sono in memoria al momento del salvataggio della soluzione.

Solo il file .sln contiene `preSolution` `postSolution` voci nelle sezioni e . Non ci sono sezioni simili nel file .suo poiché la soluzione richiede queste informazioni per il caricamento corretto. Il file con estensione suo contiene opzioni specifiche dell'utente, ad esempio note private, che non devono essere condivise o inserite nel controllo del codice sorgente.

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [File delle opzioni utente della soluzione (con estensione suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Soluzioni](../../extensibility/internals/solutions-overview.md)
