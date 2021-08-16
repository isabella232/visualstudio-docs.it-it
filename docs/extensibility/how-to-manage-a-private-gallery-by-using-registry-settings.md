---
title: Gestire una raccolta privata usando le impostazioni del Registro di sistema
description: Informazioni su come controllare l'accesso a controlli, modelli e strumenti nella raccolta Visual Studio, nella raccolta di esempi o nelle raccolte private.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e1048f5af6457d8429694c73f37e82f5b420bc66f08abd198016388441346f40
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414701"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procedura: Gestire una raccolta privata usando le impostazioni del Registro di sistema
Gli amministratori o gli sviluppatori di un'estensione Isolated Shell possono controllare l'accesso a controlli, modelli e strumenti nella raccolta Visual Studio, nella raccolta di esempi o nelle raccolte private. Per rendere disponibile o non disponibile una raccolta, creare un file *con estensione pkgdef* che descriva le chiavi del Registro di sistema modificate e i relativi valori.

## <a name="manage-private-galleries"></a>Gestire raccolte private
 È possibile creare un file *con estensione pkgdef* per controllare l'accesso alle raccolte in più computer. Questo file deve avere il formato seguente.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 La `Repositories` chiave fa riferimento alla raccolta da abilitato o disabilitato. La Visual Studio e la raccolta di esempi usano i GUID del repository seguenti:

- Visual Studio Raccolta: 0F45E408-7995-4375-9485-86B8DB553DC9

- Raccolta di esempi: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Il `Disabled` valore è facoltativo. Per impostazione predefinita, è abilitata una raccolta.

  Il `Priority` valore determina l'ordine in cui le raccolte sono elencate nella **finestra di dialogo** Opzioni . Visual Studio La raccolta ha la priorità 10 e la raccolta di esempi ha la priorità 20. Le raccolte private iniziano con la priorità 100. Se più raccolte hanno lo stesso valore di priorità, l'ordine in cui vengono visualizzate è determinato dai valori dei relativi attributi `DisplayName` localizzati.

  Il valore è obbligatorio per le raccolte basate su `Protocol` Atom o SharePoint basate su SharePoint.

  È `DisplayName` necessario specificare , o entrambi e `DisplayNameResourceID` `DisplayNamePackageGuid` . Se vengono specificati tutti, vengono usati `DisplayNameResourceID` `DisplayNamePackageGuid` la coppia e .

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Disabilitare la Visual Studio Gallery usando un file con estensione pkgdef
 È possibile disabilitare una raccolta in un file *con estensione pkgdef.* La voce seguente disabilita la raccolta Visual Studio dati:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 La voce seguente disabilita la raccolta di esempi:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Vedi anche
- [Raccolte private](../extensibility/private-galleries.md)
