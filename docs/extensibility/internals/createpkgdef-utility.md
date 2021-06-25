---
title: Utilità CreatePkgDef | Microsoft Docs
description: Informazioni sull'utilità CreatePkgDef che accetta un file .dll per un'estensione Visual Studio come parametro e crea un file con estensione pkgdef per accompagnare il file .dll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bfbd4b42d9ceddd40e08c28926a59aecba719fe9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898123"
---
# <a name="createpkgdef-utility"></a>Utilità CreatePkgDef
Accetta un .dll per un'estensione Visual Studio come parametro e crea un file con estensione *pkgdef* per accompagnare il file *.dll* file. Il file *con estensione pkgdef* contiene tutte le informazioni che verrebbero altrimenti scritte nel Registro di sistema quando viene installata l'estensione.

> [!NOTE]
> La maggior parte dei modelli di progetto inclusi in Visual Studio SDK crea automaticamente file *con estensione pkgdef* come parte del processo di compilazione. Questo documento è destinato agli utenti che vogliono creare pacchetti manualmente o convertire i pacchetti esistenti per usare *la distribuzione con estensione pkgdef.*

## <a name="syntax"></a>Sintassi

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argomenti
**/out= &lt; FileName&gt;**\
Obbligatorio. Imposta il nome del file di output *con estensione pkgdef* su &lt; FileName &gt; .

**/codebase**\
facoltativo. Forza la registrazione con **l'utilità CodeBase.**

**/assembly**\
Forza la registrazione con **l'utilità Assembly.**

**&lt;AssemblyPath&gt;**\
Percorso del file *.dll* da cui generare il *file con estensione pkgdef.*

## <a name="remarks"></a>Commenti
La distribuzione delle estensioni *tramite file con estensione pkgdef* sostituisce i requisiti del Registro di sistema delle versioni precedenti Visual Studio.

::: moniker range=">=vs-2019"

I *file con estensione pkgdef* devono essere installati in uno dei percorsi seguenti:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Se la cartella di installazione è *%localappdata%\Microsoft\Visual Studio\16.0\Extensions, \\* l'estensione viene riconosciuta da Visual Studio ma è disabilitata per impostazione predefinita. L'utente può abilitare l'estensione usando **Gestisci estensioni**.

Se la cartella di installazione è *%vsinstalldir%\Common7\IDE\Extensions, \\* l'estensione è abilitata per impostazione predefinita.

> [!NOTE]
> Lo **strumento Gestisci estensioni** non può essere usato per accedere a un'estensione a meno che non sia installato come parte di un pacchetto VSIX.

::: moniker-end

::: moniker range="vs-2017"

I *file con estensione pkgdef* devono essere installati in uno dei percorsi seguenti:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Se la cartella di installazione è *%localappdata%\Microsoft\Visual Studio\15.0\Extensions, \\* l'estensione viene riconosciuta da Visual Studio ma è disabilitata per impostazione predefinita. L'utente può abilitare l'estensione usando **Estensioni e aggiornamenti**.

Se la cartella di installazione è *%vsinstalldir%\Common7\IDE\Extensions, \\* l'estensione è abilitata per impostazione predefinita.

> [!NOTE]
> Lo **strumento Estensioni e aggiornamenti** non può essere usato per accedere a un'estensione a meno che non sia installato come parte di un pacchetto VSIX.

::: moniker-end

## <a name="see-also"></a>Vedere anche
- [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
