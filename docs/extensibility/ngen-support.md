---
title: Supporto di Ngen in VSIX v3 | Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dcf5f6366514fb18074d253b788c9cf67f1d297a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835052"
---
# <a name="ngen-support-in-vsix-v3"></a>Supporto di Ngen in VSIX v3

Con Visual Studio 2017 e il nuovo VSIX v3 estensione (versione 3) manifesto formato, l'estensione per gli sviluppatori possono ora "ngen" i relativi assembly al momento dell'installazione.

Di seguito è riportato un frammento da MSDN che spiega quali "ngen":

>Generatore di immagini Native (*Ngen.exe*) è uno strumento che consente di migliorare le prestazioni delle applicazioni gestite. *Ngen.exe* crea immagini native, che sono file che contengono codice compilato specifico del processore del computer e li installa nella cache delle immagini native nel computer locale. Il runtime può usare le immagini native della cache anziché il compilatore Just-In-Time (JIT) per compilare l'assembly originale.
>
>da [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Per poter "ngen" un assembly, il progetto VSIX deve essere installato "per ogni istanza per ogni macchina". Questa opzione può essere abilitata selezionando la casella di controllo "tutti gli utenti" `extension.vsixmanifest` progettazione:

![controllare tutti gli utenti](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Come abilitare Ngen

Per abilitare ngen per un assembly, è possibile usare la **proprietà** finestra in Visual Studio.

Esistono 4 proprietà che è possibile impostare:

1. **Ngen** (booleana) - se true, il programma di installazione di Visual Studio verrà "ngen" dell'assembly.
2. **Applicazione Ngen** (stringa) - Ngen offre l'opportunità di utilizzare un application *app* file per risolvere le dipendenze dell'assembly. Questo valore deve essere impostato su un'applicazione la cui proprietà *app. config* si desidera utilizzare (relativo alla directory di installazione di Visual Studio).
3. **Architettura Ngen** (enumerazione) - l'architettura in modo nativo compila l'assembly. Le opzioni sono: una. B NotSpecified. X86 c. X64 d. Tutti
4. **Priorità Ngen** (numero intero compreso tra 1 e 3 -) a livello di priorità di Ngen è documentato al [livelli di priorità Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Di seguito viene illustrato il **proprietà** finestra in azione:

![nelle proprietà di Ngen](media/ngen-in-properties.png)

Questo aggiungerà i metadati per il riferimento al progetto all'interno del progetto VSIX *file con estensione csproj* file:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**Nota:** Se si preferisce, è possibile modificare direttamente il file con estensione csproj.

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche di progettazione di proprietà si applicano solo ai riferimenti al progetto; è possibile impostare i metadati di Ngen per gli elementi all'interno del progetto anche (usando gli stessi metodi descritti in precedenza) fino a quando gli elementi sono assembly .NET.