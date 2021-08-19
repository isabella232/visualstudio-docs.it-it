---
description: Usare il DIA SDK per accedere alle informazioni di debug Microsoft.
title: Panoramica (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: cb3e33e6db33e7f7ea34d2133e144f88e3fc4c6bf78cd900293bbec798a77968
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121436315"
---
# <a name="overview-debug-interface-access-sdk"></a>Panoramica (Debug Interface Access SDK)
Usare il DIA SDK per accedere alle informazioni di debug Microsoft. Il DIA SDK fornisce un set di API basato su COM che elimina la necessità di riscrivere il codice ogni volta che Microsoft modifica il formato delle informazioni di debug. Il DIA SDK consente anche di leggere da un set selezionato di versioni precedenti delle informazioni di debug, che si trovano in file con estensione pdb e dbg generati dalle versioni [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 5.0 e successive.

 Ogni interfaccia nella classe DIA SDK un oggetto COM diverso, tranne quando specificato diversamente. Le interfacce aggiuntive, e quindi gli oggetti aggiuntivi, vengono create tramite query esplicite, ad esempio [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) o [IDiaSession::findChildren,](../../debugger/debug-interface-access/idiasession-findchildren.md)anziché chiamando su puntatori di interfaccia `QueryInterface` esistenti.

## <a name="see-also"></a>Vedi anche
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
