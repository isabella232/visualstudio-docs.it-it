---
title: Utilità CreatePkgDef Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709159"
---
# <a name="createpkgdef-utility"></a>Utilità CreatePkgDef
Accetta un file DLL per un'estensione di Visual Studio come parametro e crea un file *con estensione pkgdef* per accompagnare il file *DLL.* Il file *.pkgdef* contiene tutte le informazioni che altrimenti verrebbero scritte nel Registro di sistema quando viene installata l'estensione.

> [!NOTE]
> La maggior parte dei modelli di progetto inclusi in Visual Studio SDK crea automaticamente file *con estensione pkgdef* come parte del processo di compilazione. Questo documento è destinato a coloro che desiderano creare pacchetti manualmente o convertire i pacchetti esistenti per utilizzare la distribuzione *con estensione pkgdef.*

## <a name="syntax"></a>Sintassi

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argomenti
**/out:&lt;NomeFile&gt;**\
Obbligatorio. Imposta il nome del file di &lt;output&gt;con *estensione pkgdef* su NomeFile .

**/codebase**\
Facoltativa. Forza la registrazione con l'utilità **CodeBase.**

**/assembly**\
Forza la registrazione con l'utilità **Assemblaggio.**

**&lt;AssemblyPath (percorso assembly)&gt;**\
Percorso del file *DLL* da cui si desidera generare il *file pkgdef*.

## <a name="remarks"></a>Osservazioni
La distribuzione delle estensioni tramite file *con estensione pkgdef* sostituisce i requisiti del Registro di sistema delle versioni precedenti di Visual Studio.

::: moniker range=">=vs-2019"

I file *con estensione pkgdef* devono essere installati in una delle seguenti posizioni:

- *%localappdata%\\*

- *%vsinstalldir%\\*

Se la cartella di installazione è *%localappdata% , Microsoft\\Visual Studio , 16.0 ,* l'estensione viene riconosciuta da Visual Studio ma è disabilitata per impostazione predefinita. L'utente può abilitare l'estensione utilizzando **Gestisci estensioni**.

Se la cartella di installazione è *%vsinstalldir%\\, Common7 , IDE , Extensions*, l'estensione è abilitata per impostazione predefinita.

> [!NOTE]
> Lo strumento **Gestisci estensioni** non può essere utilizzato per accedere a un'estensione a meno che non sia installata come parte di un pacchetto VSIX.

::: moniker-end

::: moniker range="vs-2017"

I file *con estensione pkgdef* devono essere installati in una delle seguenti posizioni:

- *%localappdata%\\*

- *%vsinstalldir%\\*

Se la cartella di installazione è *%localappdata% , Microsoft\\Visual Studio , 15.0 ,* l'estensione viene riconosciuta da Visual Studio ma è disabilitata per impostazione predefinita. L'utente può abilitare l'estensione utilizzando **estensioni e aggiornamenti**.

Se la cartella di installazione è *%vsinstalldir%\\, Common7 , IDE , Extensions*, l'estensione è abilitata per impostazione predefinita.

> [!NOTE]
> Lo strumento **Estensioni e aggiornamenti** non può essere utilizzato per accedere a un'estensione a meno che non sia installato come parte di un pacchetto VSIX.

::: moniker-end

## <a name="see-also"></a>Vedere anche
- [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
