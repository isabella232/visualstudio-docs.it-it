---
title: -Edit (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22c5aeffae35a4202577cf8065b76b1968616355
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704291"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
Apre il file specificato in un'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="syntax"></a>Sintassi

```cmd
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>Argomenti
 `file1`

 Facoltativo. File da aprire in un'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Se non esiste alcuna istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne viene creata una nuova con un layout di finestra semplificato e `file1` viene aperto nella nuova istanza.

 `file2`

 Facoltativo. Uno o più file aggiuntivi da aprire nell'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="remarks"></a>Note
 Se non è stato specificato alcun file ed è presente un'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] riceve lo stato attivo. Se non è stato specificato alcun file e non è presente un'istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], verrà creata una nuova istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con un layout di finestra semplificato.

 Se l'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è in uno stato modale, ad esempio, se la [finestra di dialogo Opzioni](../../ide/reference/options-dialog-box-visual-studio.md) è aperta, il file verrà aperto nell'istanza esistente quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esce dallo stato modale.

## <a name="example"></a>Esempio
 In questo esempio il file `MyFile.cs` viene aperto in un'istanza esistente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] oppure in una nuova istanza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se non ne esiste ancora una.

```cmd
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Vedere anche

- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)