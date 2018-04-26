---
title: Comando ShowWebBrowser
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c1396cd28244a655d18f6e09f4795dd099a11ca7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="showwebbrowser-command"></a>Comando ShowWebBrowser
Visualizza l'URL specificato in una finestra del Web browser all'interno o all'esterno dell'ambiente di sviluppo integrato (IDE).

## <a name="syntax"></a>Sintassi

```
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argomenti
 `URL`

 Obbligatorio. URL (Uniform Resource Locator) per il sito Web.

## <a name="switches"></a>Opzioni
 /new

 Facoltativo. Specifica che la pagina venga visualizzata in una nuova istanza del Web browser.

 /ext

 Facoltativo. Specifica che la pagina venga visualizzata nel Web browser predefinito all'esterno dell'IDE.

## <a name="remarks"></a>Note
 L'alias per il comando **ShowWebBrowser** è **navigate** o **nav**.

## <a name="example"></a>Esempio
 L'esempio seguente illustra la home page di MSDN Online in un Web browser all'esterno dell'IDE. Se è già aperta un'istanza del Web browser, viene usata; in caso contrario, viene avviata una nuova istanza.

```
>View.ShowWebBrowser http://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Vedere anche

- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Finestra di comando](../../ide/reference/command-window.md)
- [Casella Trova/Comando](../../ide/find-command-box.md)
- [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)