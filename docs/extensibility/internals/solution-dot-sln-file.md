---
title: Soluzione (. File sln
description: Informazioni sul file sln, ovvero uno dei file che mantiene le informazioni sullo stato per un progetto in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/15/2019
ms.topic: conceptual
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 97071500b8f3bc6cb4d6c21d264646cac2e7fdb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962925"
---
# <a name="solution-sln-file"></a>File di soluzione (. sln)

Una soluzione è una struttura per organizzare i progetti in Visual Studio. La soluzione mantiene le informazioni sullo stato per i progetti in due file:

- file con estensione sln (basato su testo, condiviso)

- file con estensione suo (opzioni binarie della soluzione specifica dell'utente)

Per ulteriori informazioni sui file con estensione suo, vedere [Opzioni utente soluzione (. Suo) file](../../extensibility/internals/solution-user-options-dot-suo-file.md).

Se il pacchetto VSPackage viene caricato come risultato del riferimento nel file con estensione sln, l'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> per leggere il file con estensione sln.

Il file con estensione sln contiene informazioni basate su testo utilizzate dall'ambiente per trovare e caricare i parametri del valore del nome per i dati salvati in modo permanente e i pacchetti VSPackage a cui fa riferimento. Quando un utente apre una soluzione, l'ambiente esegue il ciclo `preSolution` delle `Project` informazioni, e `postSolution` nel file con estensione sln per caricare la soluzione, i progetti all'interno della soluzione e tutte le informazioni salvate in modo permanente collegate alla soluzione.

Il file di ogni progetto contiene informazioni aggiuntive lette dall'ambiente per popolare la gerarchia con gli elementi del progetto. La persistenza dei dati della gerarchia è controllata dal progetto. I dati non vengono in genere archiviati nel file con estensione sln, sebbene sia possibile scrivere intenzionalmente le informazioni sul progetto nel file con estensione sln se si sceglie di eseguire questa operazione. Per ulteriori informazioni sulla persistenza, vedere [persistenza del progetto](../../extensibility/internals/project-persistence.md) e [apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="file-header"></a>Intestazione del file

L'intestazione di un file con estensione sln ha un aspetto simile al seguente:

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
La versione principale di Visual Studio che (più di recente) ha salvato il file di soluzione. Queste informazioni controllano il numero di versione nell'icona della soluzione.

`VisualStudioVersion = 15.0.26730.15`\
La versione completa di Visual Studio che (più di recente) ha salvato il file di soluzione. Se il file della soluzione viene salvato con una versione più recente di Visual Studio con la stessa versione principale, questo valore non viene aggiornato in modo da ridurre la varianza nei file di soluzione.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Versione minima (meno recente) di Visual Studio in grado di aprire il file di soluzione.

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
La versione principale di Visual Studio che (più di recente) ha salvato il file di soluzione. Queste informazioni controllano il numero di versione nell'icona della soluzione.

`VisualStudioVersion = 16.0.28701.123`\
La versione completa di Visual Studio che (più di recente) ha salvato il file di soluzione. Se il file della soluzione viene salvato con una versione più recente di Visual Studio con la stessa versione principale, questo valore non viene aggiornato in modo da ridurre la varianza del file.

`MinimumVisualStudioVersion = 10.0.40219.1`\
Versione minima (meno recente) di Visual Studio in grado di aprire il file di soluzione.

::: moniker-end

## <a name="file-body"></a>Corpo del file

Il corpo di un file con estensione sln è costituito da diverse sezioni con etichetta `GlobalSection` , come la seguente:

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

1. L'ambiente legge la sezione globale del file con estensione sln ed elabora tutte le sezioni contrassegnate come `preSolution` . In questo file di esempio è presente un'istruzione di questo tipo:

   ```
   GlobalSection(SolutionConfiguration) = preSolution
        ConfigName.0 = Debug
        ConfigName.1 = Release
   ```

   Quando l'ambiente legge il `GlobalSection('name')` tag, il nome viene mappato a un VSPackage usando il registro di sistema. Il nome della chiave deve esistere nel registro di sistema in [HKLM \\<Application ID registro radice \> \SolutionPersistence\AggregateGUIDs]. Il valore predefinito delle chiavi è il GUID del pacchetto (REG_SZ) del pacchetto VSPackage che ha scritto le voci.

2. L'ambiente carica il pacchetto VSPackage, chiama il `QueryInterface` pacchetto VSPackage per l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interfaccia e chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> metodo con i dati nella sezione in modo che il pacchetto VSPackage possa archiviare i dati. L'ambiente ripete questo processo per ogni `preSolution` sezione.

3. L'ambiente scorre i blocchi di persistenza del progetto. In questo caso, è presente un progetto.

   ```
   Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",
   "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"
   EndProject
   ```

   Questa istruzione contiene il GUID del progetto univoco e il GUID del tipo di progetto. Queste informazioni vengono usate dall'ambiente per trovare il file o i file di progetto appartenenti alla soluzione e il pacchetto VSPackage necessario per ogni progetto. Il GUID del progetto viene passato a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> per caricare il VSPackage specifico correlato al progetto, quindi il progetto viene caricato dal pacchetto VSPackage. In questo caso, il pacchetto VSPackage caricato per questo progetto viene Visual Basic.

   Ogni progetto può rendere permanente un ID istanza di progetto univoco, in modo che sia possibile accedervi in base alle esigenze di altri progetti nella soluzione. Idealmente, se la soluzione e i progetti sono sotto il controllo del codice sorgente, il percorso del progetto deve essere relativo al percorso della soluzione. Quando la soluzione viene caricata per la prima volta, i file di progetto non possono trovarsi nel computer dell'utente. Se il file di progetto è archiviato nel server relativo al file della soluzione, è relativamente semplice trovare e copiare il file di progetto nel computer dell'utente. Viene quindi copiato e caricato il resto dei file necessari per il progetto.

4. In base alle informazioni contenute nella sezione del progetto del file con estensione sln, l'ambiente carica ogni file di progetto. Il progetto stesso è quindi responsabile del popolamento della gerarchia del progetto e del caricamento di tutti i progetti annidati.

5. Dopo l'elaborazione di tutte le sezioni del file con estensione sln, la soluzione viene visualizzata in Esplora soluzioni ed è pronta per essere modificata dall'utente.

Se non è possibile caricare un pacchetto VSPackage che implementa un progetto nella soluzione, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> viene chiamato il metodo e a ogni altro progetto della soluzione viene data la possibilità di ignorare le modifiche che potrebbero essere state apportate durante il caricamento. Se si verificano errori di analisi, la maggior parte delle informazioni possibile viene mantenuta con i file della soluzione e l'ambiente Visualizza una finestra di dialogo che avvisa l'utente che la soluzione è danneggiata.

Quando la soluzione viene salvata o chiusa, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> metodo viene chiamato e passato alla gerarchia per verificare se sono state apportate modifiche alla soluzione che devono essere immesse nel file con estensione sln. Un valore null, passato a `QuerySaveSolutionProps` in <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> , indica che le informazioni vengono rese permanente per la soluzione. Se il valore non è null, le informazioni salvate in modo permanente sono relative a un progetto specifico, determinato dal puntatore all' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia.

Se sono presenti informazioni da salvare, l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> interfaccia viene chiamata con un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> metodo. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> metodo viene quindi chiamato dall'ambiente per recuperare le coppie nome/valore dall' `IPropertyBag` interfaccia e scrivere le informazioni nel file con estensione sln.

`SaveSolutionProps``WriteSolutionProps`gli oggetti e vengono chiamati in modo ricorsivo dall'ambiente per recuperare le informazioni da salvare dall' `IPropertyBag` interfaccia fino a quando non sono state immesse tutte le modifiche nel file con estensione sln. In questo modo, è possibile garantire che le informazioni vengano rese permanente con la soluzione e disponibili alla successiva apertura della soluzione.

Ogni VSPackage caricato viene enumerato per verificare se è presente qualcosa da salvare nel file con estensione sln. È solo in fase di caricamento in cui vengono eseguite query sulle chiavi del registro di sistema. L'ambiente è a conoscenza di tutti i pacchetti caricati perché sono in memoria al momento del salvataggio della soluzione.

Solo il file con estensione sln contiene voci nelle `preSolution` `postSolution` sezioni e. Non sono presenti sezioni simili nel file con estensione suo poiché la soluzione richiede che queste informazioni vengano caricate correttamente. Il file con estensione suo contiene opzioni specifiche dell'utente, ad esempio note private, che non sono progettate per essere condivise o inserite nel controllo del codice sorgente.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- [File delle opzioni utente della soluzione (con estensione suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)
- [Soluzioni](../../extensibility/internals/solutions-overview.md)
