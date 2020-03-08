---
title: File di risposta MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- response files, MSBuild
- MSBuild, response files
- MSBuild, .rsp files
- .rsp files
ms.assetid: 9f53987b-20ee-470a-ab62-fce997bb5e15
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44d6e3c77fee53b15ec8d18cb74fd7355ee101a8
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410018"
---
# <a name="msbuild-response-files"></a>File di risposta MSBuild

I file di risposta (con estensione *rsp*) sono file di testo che contengono opzioni della riga di comando di *MSBuild.exe*. Ogni opzione può essere su una riga separata oppure tutte le opzioni possono essere sulla stessa riga. Le righe di commento sono precedute da un simbolo **#** . L'opzione **@** viene usata per passare un altro file di risposta a *MSBuild.exe*.

## <a name="msbuildrsp"></a>MSBuild.rsp

Il file di risposta automatica è un file speciale con estensione *rsp* usato automaticamente da *MSBuild.exe* durante la compilazione di un progetto. Il file *MSBuild.rsp* si deve trovare nella stessa directory di *MSBuild.exe*, in caso contrario non sarà rilevato. È possibile modificare questo file per specificare opzioni predefinite della riga di comando per *MSBuild.exe*. Ad esempio, se si usa lo stesso logger ogni volta che si compila un progetto, è possibile aggiungere l'opzione **-logger** a *MSBuild.rsp* perché *MSBuild.exe* usi il logger ogni volta che viene compilato un progetto.

## <a name="directorybuildrsp"></a>Directory.Build.rsp

Nella versione 15.6 e successive MSBuild cercherà un file denominato *Directory.Build.rsp*. nelle directory padre del progetto.  Questo file può risultare utile in un repository di codice sorgente per la visualizzazione degli argomenti predefiniti durante le compilazioni da riga di comando.  Può anche essere usato per specificare gli argomenti della riga di comando delle build ospitate.

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
- [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md)
