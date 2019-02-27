---
title: Panoramica (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e459d4429d712a9ca4c245d581c6be3578711cd6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616752"
---
# <a name="overview-debug-interface-access-sdk"></a>Panoramica (Debug Interface Access SDK)
Usare il DIA SDK per accedere alle informazioni di debug di Microsoft. Il DIA SDK fornisce una COM basati su set di API che elimina la necessità di riscrivere il codice ogni volta che Microsoft cambia il formato delle informazioni di debug. Il DIA SDK consente anche di leggere da un set selezionato di versioni precedenti di informazioni di debug, che si trova nel file DBG e PDB generati da [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 5.0 e versioni successive.

 Ogni interfaccia in DIA SDK rappresenta un oggetto COM diverso, ad eccezione di dove indicato. Interfacce aggiuntive e pertanto gli oggetti aggiuntivi, vengono creati tramite query esplicita, ad esempio [Idiadatasource](../../debugger/debug-interface-access/idiadatasource-opensession.md) oppure [Findchildren](../../debugger/debug-interface-access/idiasession-findchildren.md), piuttosto che dalla chiamata `QueryInterface` sui puntatori di interfaccia esistente.

## <a name="see-also"></a>Vedere anche
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)