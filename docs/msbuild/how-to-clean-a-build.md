---
title: 'Procedura: Pulire una compilazione | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1dab142315a7d243caf6604c5f2745244ff166e2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027932"
---
# <a name="how-to-clean-a-build"></a>Procedura: Pulire una compilazione
Quando si esegue la pulitura di una compilazione, vengono eliminati tutti i file intermedi e di output, lasciando solo i file di progetto e di componente. È quindi possibile compilare nuove istanze di file intermedi e di output dai file di progetto e di componente. La libreria di attività comuni fornita con [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] include un'attività [Exec](../msbuild/exec-task.md) che è possibile usare per eseguire i comandi di sistema. Per altre informazioni sulla libreria di attività, vedere [Attività MSBuild](../msbuild/msbuild-task-reference.md).  
  
## <a name="create-a-directory-for-output-items"></a>Creare una directory per gli elementi di output  
 Per impostazione predefinita, il file con estensione *exe* creato quando si compila un progetto viene inserito nella stessa directory dei file di progetto e di origine. Gli elementi di output invece vengono in genere creati in una directory distinta.  
  
#### <a name="to-create-a-directory-for-output-items"></a>Per creare una directory per gli elementi di output  
  
1.  Usare l'elemento `Property` per definire il percorso e il nome della directory. Ad esempio, creare una directory denominata *BuiltApp* nella directory che contiene i file di progetto e di origine:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Usare l'attività [MakeDir](../msbuild/makedir-task.md) per creare la directory se la directory non esiste. Ad esempio:  
  
     ```xml
     <MakeDir Directories = "$(builtdir)"  
      Condition = "!Exists('$(builtdir)')" />
     ```
  
## <a name="remove-the-output-items"></a>Rimuovere gli elementi di output  
 Prima di creare nuove istanze dei file intermedi e di output, è possibile cancellare tutte le istanze precedenti dei file intermedi e di output. Usare l'attività [RemoveDir](../msbuild/removedir-task.md) per eliminare una directory e tutti i file e le directory in essa contenuti da un disco.  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Per rimuovere una directory e tutti i file contenuti nella directory  
  
-   Usare l'attività `RemoveDir` per rimuovere la directory. Ad esempio:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>Esempio  
 Il progetto di esempio di codice seguente contiene una nuova destinazione, `Clean`, che usa l'attività `RemoveDir` per eliminare una directory e tutti i file e le directory in essa contenute. Anche in questo esempio, la destinazione `Compile` crea una directory distinta per gli elementi di output che vengono eliminati durante la pulizia della compilazione.  
  
 `Compile` è definito come destinazione predefinita che viene usata automaticamente se non vengono specificate una o più destinazioni diverse. Usare l'opzione della riga di comando **-target** per specificare una destinazione diversa. Ad esempio:  
  
 `msbuild <file name>.proj -target:Clean`  
  
 L'opzione **-target** può essere abbreviata in **-t** e può specificare più di una destinazione. Ad esempio, per usare la destinazione `Clean` e quindi la destinazione `Compile`, digitare:  
  
 `msbuild <file name>.proj -t:Clean;Compile`  
  
```xml  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Attività Exec](../msbuild/exec-task.md)   
 [Attività MakeDir](../msbuild/makedir-task.md)   
 [Attività RemoveDir](../msbuild/removedir-task.md)   
 [Attività Csc](../msbuild/csc-task.md)   
 [Destinazioni](../msbuild/msbuild-targets.md)