---
title: 'Procedura: Gestire una raccolta privata utilizzando le impostazioni del Registro di sistema Documenti Microsoft'
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
ms.openlocfilehash: a2630fc71bea40a4d05e616ae336759ba62431a0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710925"
---
# <a name="how-to-manage-a-private-gallery-by-using-registry-settings"></a>Procedura: gestire una raccolta privata utilizzando le impostazioni del Registro di sistemaHow to: Manage a private gallery by using registry settings
Gli amministratori o gli sviluppatori di un'estensione Isolated Shell possono controllare l'accesso ai controlli, ai modelli e agli strumenti di Visual Studio Gallery, della raccolta di esempi o delle raccolte private. Per rendere una raccolta disponibile o non disponibile, creare un file *con estensione pkgdef* che descriva le chiavi del Registro di sistema modificate e i relativi valori.

## <a name="manage-private-galleries"></a>Gestire gallerie private
 È possibile creare un file *.pkgdef* per controllare l'accesso alle gallerie su più computer. Questo file deve avere il seguente formato.

```
[$RootKey$\ExtensionManager\Repositories\{UniqueGUID}]
@={URI}  (REG_SZ)
Disabled=0 | 1 (DWORD)
Priority=0 (highest priority) ... MaxInt (lowest priority) (DWORD) (uint)
Protocol=Atom Feed|Sharepoint (REG_SZ)
DisplayName={DisplayName} (REG_SZ)
DisplayNameResourceID={ID} (REG_SZ)
DisplayNamePackageGuid={GUID} (REG_SZ)

```

 La `Repositories` chiave si riferisce alla raccolta da abilitare o disabilitare. The Visual Studio Gallery and the Samples Gallery use the following repository GUIDs:

- Raccolta di Visual Studio : 0F45E408-7995-4375-9485-86B8DB553DC9

- Raccolta di campioni : AEB9CB40-D8E6-4615-B52C-27E307F8506C

  Il `Disabled` valore è facoltativo. Per impostazione predefinita, una raccolta è abilitata.

  Il `Priority` valore determina l'ordine in cui le raccolte sono elencate nella finestra di dialogo **Opzioni.** Visual Studio Gallery ha la priorità 10 e la raccolta di esempi ha priorità 20.Visual Studio Gallery has priority 10 and the Samples Gallery has priority 20. Le gallerie private partono dalla priorità 100. Se più raccolte hanno lo stesso valore di priorità, l'ordine in `DisplayName` cui vengono visualizzate è determinato dai valori dei relativi attributi localizzati.

  Il `Protocol` valore è obbligatorio per le raccolte basate su Atom o SharePoint.The value is required for Atom-based or SharePoint-based galleries.

  È `DisplayName`necessario `DisplayNameResourceID` specificare , o entrambi e `DisplayNamePackageGuid`,. Se vengono specificati tutti, viene utilizzata la `DisplayNameResourceID` coppia e `DisplayNamePackageGuid` .

## <a name="disable-the-visual-studio-gallery-using-a-pkgdef-file"></a>Disabilitare Visual Studio Gallery usando un file con estensione pkgdef
 È possibile disabilitare una raccolta in un file *con estensione pkgdef.* La voce seguente disabilita Visual Studio Gallery:

```
[$RootKey$\ExtensionManager\Repositories\{0F45E408-7995-4375-9485-86B8DB553DC9}]
"Disabled"=dword:00000001

```

 La seguente voce disabilita la raccolta di esempi:

```
[$RootKey$\ExtensionManager\Repositories\{AEB9CB40-D8E6-4615-B52C-27E307F8506C}]
"Disabled"=dword:00000001

```

## <a name="see-also"></a>Vedere anche
- [Gallerie private](../extensibility/private-galleries.md)
