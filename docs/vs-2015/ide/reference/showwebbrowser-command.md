---
title: Comando ShowWebBrowser| Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1ecf86bdc7516f05935bd944f23633b3baad2c7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663513"
---
# <a name="showwebbrowser-command"></a>Comando ShowWebBrowser
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visualizza l'URL specificato in una finestra del Web browser all'interno o all'esterno dell'ambiente di sviluppo integrato (IDE).

## <a name="syntax"></a>Sintassi

```
View.ShowWebBrowser URL [/new][/ext]
```

## <a name="arguments"></a>Argomenti
 `URL` Obbligatorio. URL (Uniform Resource Locator) per il sito Web.

## <a name="switches"></a>Commutatori
 /New facoltativo. Specifica che la pagina venga visualizzata in una nuova istanza del Web browser.

 /ext Facoltativo. Specifica che la pagina venga visualizzata nel Web browser predefinito all'esterno dell'IDE.

## <a name="remarks"></a>Osservazioni
 L'alias per il comando **ShowWebBrowser** è **navigate** o **nav**.

## <a name="example"></a>Esempio
 L'esempio seguente illustra la home page di MSDN Online in un Web browser all'esterno dell'IDE. Se è già aperta un'istanza del Web browser, viene usata; in caso contrario, viene avviata una nuova istanza.

```
>View.ShowWebBrowser https://msdn.microsoft.com /ext
```

## <a name="see-also"></a>Vedere anche
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md) [finestra](../../ide/reference/command-window.md) di comando [Trova/comando riquadro](../../ide/find-command-box.md) di [Visual Studio alias di comando](../../ide/reference/visual-studio-command-aliases.md)
