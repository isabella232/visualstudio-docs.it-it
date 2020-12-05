---
title: Impostazioni predefinite di Visual Basic, Progetti, finestra di dialogo Opzioni
description: Informazioni su come usare la pagina impostazioni predefinite Visual Basic nella sezione progetti e soluzioni per specificare le impostazioni predefinite per le opzioni del progetto Visual Basic.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f761161f2ad29be994b3a6260bafe827a41fabe0
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616356"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Impostazioni predefinite di Visual Basic, Progetti, finestra di dialogo Opzioni
Specifica le impostazioni predefinite per le opzioni dei progetti Visual Basic. Alla creazione di un nuovo progetto, le istruzioni specificate per le opzioni verranno aggiunte all'intestazione del progetto nell'editor di codice. Le opzioni si applicano a tutti i progetti Visual Basic.

Per accedere a questa finestra di dialogo, nel menu **Strumenti** fare clic su **Opzioni**, espandere la cartella **Progetti e soluzioni** e quindi fare clic su **Impostazioni predefinite di Visual Basic**.

 **Option Explicit**

Imposta il valore predefinito del compilatore in modo da richiedere le dichiarazioni esplicite delle variabili. Per impostazione predefinita, **Option Explicit** è impostato su **On**. Per altre informazioni, vedere [/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).

 **Option Strict**

Imposta il valore predefinito del compilatore in modo da richiedere le conversioni esplicite verso un tipo di dati più piccolo e da non consentire l'associazione tardiva. Per impostazione predefinita, **Option Strict** è impostato su **Off**. Per altre informazioni, vedere [/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).

 **Option Compare**

Imposta il valore predefinito del compilatore per i confronti tra stringhe: binario (maiuscole/minuscole) o testo (senza distinzione tra maiuscole e minuscole). Per impostazione predefinita, **Option Compare** è impostato su **Binary**. Per altre informazioni, vedere [/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).

 **Option Infer**

Imposta il valore predefinito del compilatore per l'inferenza del tipo di variabile locale. Per impostazione predefinita, **Option Infer** è impostato su **On** per i nuovi progetti e su **Off** per i progetti creati nelle versioni precedenti di Visual Basic dei quali è stata eseguita la migrazione. Per altre informazioni, vedere [/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).

## <a name="see-also"></a>Vedere anche

- [Soluzioni e progetti](../../ide/solutions-and-projects-in-visual-studio.md)
