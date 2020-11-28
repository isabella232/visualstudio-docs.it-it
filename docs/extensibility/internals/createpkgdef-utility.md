---
title: Utilità CreatePkgDef | Microsoft Docs
description: Informazioni sull'utilità CreatePkgDef che accetta un file dll per un'estensione di Visual Studio come parametro e crea un file con estensione pkgdef per accompagnare il file dll.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: aa0b0e3e8ea59ce1d41f9d8a6c056239f2bc0e9a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305541"
---
# <a name="createpkgdef-utility"></a>Utilità CreatePkgDef
Accetta un file con estensione dll per un'estensione di Visual Studio come parametro e crea un file *pkgdef* per accompagnare il file *dll* . Il file *. pkgdef* contiene tutte le informazioni che altrimenti verrebbero scritte nel registro di sistema durante l'installazione dell'estensione.

> [!NOTE]
> La maggior parte dei modelli di progetto inclusi in Visual Studio SDK crea automaticamente i file con *estensione pkgdef* come parte del processo di compilazione. Questo documento è destinato agli utenti che desiderano creare pacchetti manualmente o a convertire i pacchetti esistenti in modo da usare la distribuzione *. pkgdef*  .

## <a name="syntax"></a>Sintassi

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Argomenti
**/out = &lt; nomefile&gt;**\
Obbligatorio. Imposta il nome del file di output con *estensione pkgdef* su &lt; filename &gt; .

**/codebase**\
facoltativo. Forza la registrazione con l'utilità **codebase** .

**/assembly**\
Forza la registrazione con l'utilità di **assembly** .

**&lt;AssemblyPath&gt;**\
Percorso del file con *estensione dll* da cui si desidera generare il file con *estensione pkgdef*.

## <a name="remarks"></a>Commenti
La distribuzione di estensioni con i file *pkgdef* sostituisce i requisiti del registro di sistema delle versioni precedenti di Visual Studio.

::: moniker range=">=vs-2019"

I file con *estensione pkgdef* devono essere installati in uno dei percorsi seguenti:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Se la cartella di installazione è *%LocalAppData%\Microsoft\Visual \\ Studio\16.0\Extensions*, l'estensione viene riconosciuta da Visual Studio, ma è disabilitata per impostazione predefinita. L'utente può abilitare l'estensione usando **Gestisci estensioni**.

Se la cartella di installazione *è \\ %VSInstallDir%\Common7\IDE\Extensions*, l'estensione è abilitata per impostazione predefinita.

> [!NOTE]
> Non è possibile usare lo strumento **Gestisci estensioni** per accedere a un'estensione a meno che non sia installato come parte di un pacchetto VSIX.

::: moniker-end

::: moniker range="vs-2017"

I file con *estensione pkgdef* devono essere installati in uno dei percorsi seguenti:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Se la cartella di installazione è *%LocalAppData%\Microsoft\Visual \\ Studio\15.0\Extensions*, l'estensione viene riconosciuta da Visual Studio, ma è disabilitata per impostazione predefinita. L'utente può abilitare l'estensione tramite **estensioni e aggiornamenti**.

Se la cartella di installazione *è \\ %VSInstallDir%\Common7\IDE\Extensions*, l'estensione è abilitata per impostazione predefinita.

> [!NOTE]
> Lo strumento **estensioni e aggiornamenti** non può essere usato per accedere a un'estensione a meno che non sia installato come parte di un pacchetto VSIX.

::: moniker-end

## <a name="see-also"></a>Vedere anche
- [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
