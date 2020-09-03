---
title: Panoramica (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7374b03da42e34e8ac3be8c7cc570769d9cfd1ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179204"
---
# <a name="overview-debug-interface-access-sdk"></a>Panoramica (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usare il DIA SDK per accedere alle informazioni di debug Microsoft. Il DIA SDK fornisce un set di API basato su COM che elimina la necessità di riscrivere il codice ogni volta che il formato delle informazioni di debug viene modificato da Microsoft. Il DIA SDK consente inoltre di leggere da un set selezionato di versioni precedenti delle informazioni di debug, che si trovano nei file con estensione PDB e DBG generati dalle [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] versioni 5,0 e successive.  
  
 Ogni interfaccia nel DIA SDK rappresenta un oggetto COM diverso, tranne se diversamente specificato. Le interfacce aggiuntive e quindi gli oggetti aggiuntivi vengono creati tramite query esplicite, ad esempio [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) o [IDiaSession:: findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), anziché chiamando `QueryInterface` sui puntatori di interfaccia esistenti.  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
