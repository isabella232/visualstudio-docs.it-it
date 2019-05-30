---
title: Utilità CreatePkgDef | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ab5866949d6ccfa9f3b1037abf7801ce40ace3d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332277"
---
# <a name="createpkgdef-utility"></a>Utilità CreatePkgDef
Accetta un file con estensione dll per un'estensione di Visual Studio come parametro e crea un *pkgdef* file di accompagnamento per il *DLL* file. Il *pkgdef* file contiene tutte le informazioni che verrebbe scritto nel Registro di sistema in caso contrario, quando è installata l'estensione.

> [!NOTE]
> Creare la maggior parte dei modelli di progetto che sono inclusi automaticamente in Visual Studio SDK *pkgdef* file come parte del processo di compilazione. Questo documento è destinato a utenti che desiderano creare manualmente i pacchetti o convertire i pacchetti esistenti per usare *pkgdef* distribuzione.

## <a name="syntax"></a>Sintassi

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argomenti
**/out=&lt;FileName&gt;** \
Obbligatorio. Imposta il nome del *pkgdef* del file di output &lt;FileName&gt;.

**/codebase**\
Facoltativo. Forza la registrazione con il **CodeBase** utilità.

**/assembly**\
Forza la registrazione con il **Assembly** utilità.

**&lt;AssemblyPath&gt;** \
Il percorso dei *. dll* file da cui si desidera generare il *pkgdef*.

## <a name="remarks"></a>Note
Distribuzione di un'estensione usando *pkgdef* file sostituisce i requisiti del Registro di sistema le versioni precedenti di Visual Studio.

::: moniker range=">=vs-2019"

Il *pkgdef* file devono essere installati in una delle seguenti posizioni:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%VSInstallDir%\Common7\IDE\Extensions\\*

Se la cartella di installazione *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\* , l'estensione viene riconosciuto da Visual Studio, ma è disabilitata per impostazione predefinita. L'utente può abilitare l'estensione usando **gestire le estensioni**.

Se la cartella di installazione *%vsinstalldir%\Common7\IDE\Extensions\\* , l'estensione sia abilitata per impostazione predefinita.

> [!NOTE]
> Il **gestire le estensioni** strumento non può essere usato per accedere a un'estensione a meno che non viene installato come parte di un pacchetto VSIX.

::: moniker-end

::: moniker range="vs-2017"

Il *pkgdef* file devono essere installati in una delle seguenti posizioni:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%VSInstallDir%\Common7\IDE\Extensions\\*

Se la cartella di installazione *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\* , l'estensione viene riconosciuto da Visual Studio, ma è disabilitata per impostazione predefinita. L'utente può abilitare l'estensione usando **estensioni e aggiornamenti**.

Se la cartella di installazione *%vsinstalldir%\Common7\IDE\Extensions\\* , l'estensione sia abilitata per impostazione predefinita.

> [!NOTE]
> Il **estensioni e aggiornamenti** strumento non può essere usato per accedere a un'estensione a meno che non viene installato come parte di un pacchetto VSIX.

::: moniker-end

## <a name="see-also"></a>Vedere anche
- [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
