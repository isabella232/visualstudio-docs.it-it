---
title: Gestire una raccolta privata con le impostazioni del registro di sistema
description: Informazioni su come controllare l'accesso ai controlli, i modelli e gli strumenti in Visual Studio Gallery, nella raccolta di esempi o nelle raccolte private.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX private galleries, managing
- managing VSIX private galleries
ms.assetid: 86b86442-4293-4cad-9fe2-876eef65f426
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d15d845f07310e3efcba6f05538a2207d9c416e4
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994009"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procedura: gestire una raccolta privata utilizzando le impostazioni del registro di sistema
Se si è un amministratore o lo sviluppatore di un'estensione della shell isolata, è possibile controllare l'accesso ai controlli, ai modelli e agli strumenti di Visual Studio Gallery, della raccolta di esempi o delle raccolte private. Per rendere una raccolta disponibile o non disponibile, creare un file con *estensione pkgdef* che descrive le chiavi del registro di sistema modificate e i relativi valori.

## <a name="manage-private-galleries"></a>Gestire le raccolte private
 È possibile creare un file con *estensione pkgdef* per controllare l'accesso alle raccolte su più computer. Questo file deve avere il formato seguente.

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

 La `Repositories` chiave fa riferimento alla raccolta da abilitare o disabilitare. Visual Studio Gallery e la raccolta di esempi usano i seguenti GUID del repository:

- Raccolta di Visual Studio: 0F45E408-7995-4375-9485-86B8DB553DC9

- Raccolta di esempi: AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Il `Disabled` valore è facoltativo. Per impostazione predefinita, la raccolta è abilitata.

  Il `Priority` valore determina l'ordine in cui le raccolte sono elencate nella finestra di dialogo **Opzioni** . Visual Studio Gallery ha la priorità 10 e la raccolta di esempi ha priorità 20. Le raccolte private iniziano con la priorità 100. Se più raccolte hanno lo stesso valore di priorità, l'ordine in cui vengono visualizzate è determinato dai valori degli attributi localizzati `DisplayName` .

  Il `Protocol` valore è obbligatorio per le raccolte basate su Atom o su SharePoint.

  `DisplayName` `DisplayNameResourceID` È necessario specificare sia, sia che `DisplayNamePackageGuid` . Se vengono specificati tutti, `DisplayNameResourceID` `DisplayNamePackageGuid` viene utilizzata la coppia e.

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Disabilitare Visual Studio Gallery usando un file con estensione pkgdef
 È possibile disabilitare una raccolta in un file con *estensione pkgdef* . La voce seguente Disabilita Visual Studio Gallery:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 La seguente voce Disabilita la raccolta di esempi:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Vedere anche
- [Raccolte private](../extensibility/private-galleries.md)
