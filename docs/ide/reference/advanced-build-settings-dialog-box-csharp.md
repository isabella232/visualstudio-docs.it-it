---
title: Finestra di dialogo Impostazioni di compilazione avanzate (C#)
ms.date: 08/05/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f25f9d96cd8de8dcb140c79c7dfb3a7a5981986c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595852"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Finestra di dialogo Impostazioni di compilazioneC#avanzate ()

Per specificare le proprietà di configurazione avanzate della build del progetto, usare la finestra di dialogo **Impostazioni di compilazione avanzate** di **Progettazione progetti**. Questa finestra di dialogo si C# applica solo ai progetti.

## <a name="general"></a>Generale

Le opzioni seguenti consentono di configurare le impostazioni avanzate generali.

**Versione linguaggio**

::: moniker range=">=vs-2019"

Collegamenti a [/langversion (C# opzioni del compilatore)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option), che fornisce informazioni sul modo in cui viene scelta una versione della lingua predefinita basata sul Framework di destinazione di un progetto.

::: moniker-end

::: moniker range="vs-2017"

Specifica la versione del linguaggio da usare. Il set di funzionalità varia a seconda della versione. Questa opzione può quindi essere usata per forzare il compilatore ad attivare solo un sottoinsieme delle funzionalità implementate oppure solo le funzionalità compatibili con uno standard esistente.

Il valore predefinito è C# 7,0.

::: moniker-end

**Segnalazione errori interni del compilatore**

Specifica se gli errori del compilatore devono essere segnalati a Microsoft. Se l'opzione è impostata su **prompt**, al verificarsi di un errore del compilatore interno sarà chiesto se si vuole inviare elettronicamente a Microsoft una segnalazione errori. Se è impostata su **send**, sarà inviata automaticamente una segnalazione errori. Se è impostata su **queue**, le segnalazioni errori saranno accodate. Se è impostata su **none**, l'errore sarà segnalato soltanto nell'output di testo del compilatore. Per altre informazioni, vedere [/errorreport (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option).

**Controlla overflow/underflow aritmetico**

Specifica se un'istruzione aritmetica intera non inclusa nell'ambito della parola chiave [checked](/dotnet/csharp/language-reference/keywords/checked) o [unchecked](/dotnet/csharp/language-reference/keywords/unchecked) e che restituisce un valore al di fuori dell'intervallo del tipo di dati causerà un'eccezione in fase di esecuzione. Per altre informazioni, vedere [/checked (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/checked-compiler-option).

**Ometti riferimenti a mscorlib.dll**

Specifica se nel programma verrà importato il file mscorlib.dll per l'intero spazio dei nomi <xref:System>. Selezionare questa casella se si vuole definire o creare lo spazio dei nomi <xref:System> e gli oggetti personalizzati. Per altre informazioni, vedere [/nostdlib (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/nostdlib-compiler-option).

## <a name="output"></a>Output

Le opzioni seguenti consentono di specificare impostazioni di output avanzate.

**Informazione di debug**

Specifica il tipo di informazioni di debug generate dal compilatore. Per informazioni su come configurare le prestazioni di debug di un'applicazione, vedere [Semplificazione del debug di un'immagine](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug). Per questa impostazione sono disponibili le opzioni seguenti:

- **none**

   Specifica che non saranno generate informazioni di debug.

- **full**

   Consente di associare un debugger al programma in esecuzione.

- **pdbonly**

   Consente il debug del codice sorgente quando il programma viene avviato nel debugger, ma l'assembler viene visualizzato solo se il programma in esecuzione è associato al debugger.

- **portatile**

   Crea un file con estensione pdb, vale a dire un file di simboli di tipo PE non specifico per la piattaforma che offre altri strumenti, soprattutto debugger, informazioni su cosa contiene il file eseguibile principale e come è stato generato. Vedere [Portable PDB](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (PDB portatile) per altre informazioni.

- **incorporata**

   Incorpora informazioni sui simboli di tipo PE nell'assembly. Non vengono generati file con estensione pdb esterni.

Per altre informazioni, vedere [/debug (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option).

**Allineamento file**

Specifica le dimensioni delle sezioni nel file di output. I valori validi sono **512**, **1024**, **2048**, **4096** e **8192**. Questi valori sono misurati in byte. Ogni sezione sarà allineata in base a un limite multiplo di questo valore, determinando così le dimensioni del file di output. Per altre informazioni, vedere [/filealign (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/filealign-compiler-option).

**Indirizzo di base DLL**

Specifica l'indirizzo di base preferenziale in cui caricare una DLL. L'indirizzo di base predefinito per una DLL viene impostato dal Common Language Runtime di .NET Framework. Per altre informazioni, vedere [/baseaddress (Opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/baseaddress-compiler-option).

## <a name="see-also"></a>Vedere anche

- [Opzioni del compilatore C#](/dotnet/csharp/language-reference/compiler-options/index)
- [Pagina Compilazione, Creazione progetti (C#)](../../ide/reference/build-page-project-designer-csharp.md)
