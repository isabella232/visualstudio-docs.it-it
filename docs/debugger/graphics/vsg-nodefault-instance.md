---
description: Definisce in base alla sua presenza se viene fornita un'istanza predefinita della classe VsgDbg, che fornisce l'interfaccia di acquisizione a livello di codice.
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eccdd71c66a9f25e1b0a26f4ea851bcccb738a0b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155246"
---
# <a name="vsg_nodefault_instance"></a>VSG_NODEFAULT_INSTANCE
Definisce in base alla sua presenza se viene fornita un'istanza predefinita della classe [VsgDbg](vsgdbg-class.md) , che fornisce l'interfaccia di acquisizione a livello di codice.

## <a name="syntax"></a>Sintassi

```C++
#define VSG_NODEFAULT_INSTANCE
```

## <a name="value"></a>Valore
 Simbolo del preprocessore che tramite la propria presenza o assenza determina se viene fornita un'istanza predefinita della classe `VsgDbg`. Se questo simbolo è definito, non viene fornita alcuna istanza predefinita della classe `VsgDbg`; in caso contrario, viene fornita e inizializzata un'istanza predefinita prima dell'esecuzione del programma.

 L'interfaccia di acquisizione programmatica viene fornita tramite un puntatore con ambito globale, `g_pVsgDbg`.

```cpp
VsgDbg *g_pVsgDbg;
```

## <a name="remarks"></a>Commenti
 L'istanza predefinita è in genere sufficiente, ma per utilizzare l'interfaccia di acquisizione programmatica in una DLL quando il dispositivo D3D è stato creato all'esterno di tale DLL, è necessario creare e gestire l'istanza personalizzata della classe `VsgDbg`. Se si sta gestendo l'interfaccia personalizzata per l'API di acquisizione in questo modo, disabilitare l'istanza predefinita definendo `VSG_NODEFAULT_INSTANCE` per evitare un sovraccarico.

 Se l'istanza predefinita non è disabilitata, verrà automaticamente inizializzata prima dell'esecuzione del programma e automaticamente distrutta al termine di tale programma. Non è necessario inizializzare o annullare l'inizializzazione di tale istanza in modo esplicito.

 Per disabilitare l'istanza predefinita, è necessario definire `VSG_NODEFAULT_INSTANCE` prima di includere `vsgcapture.h` nel programma.

## <a name="example"></a>Esempio
 In questo esempio viene illustrato come disabilitare l'istanza predefinita:

```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h
#define VSG_NODEFAULT_INSTANCE

#include <vsgcapture.h>
```
