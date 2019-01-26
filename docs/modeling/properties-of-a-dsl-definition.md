---
title: Proprietà di una definizione DSL
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: cdad251b4440219285ba1341663b7531634ed806
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942236"
---
# <a name="properties-of-a-dsl-definition"></a>Proprietà di una definizione DSL
Definiscono le proprietà DslDefinition *linguaggio specifico di dominio* le proprietà di definizione, ad esempio numerazione delle versioni. Vengono visualizzate le proprietà DslDefinition nelle **proprietà** finestra quando si fa clic su un'area vuota del diagramma nel *progettista del linguaggio specifico di dominio*.

 Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition presenta le proprietà nella tabella seguente:

|Proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Modificatore di accesso|Determina se il modificatore di accesso per la classe di dominio è pubblico o interno.|public|
|Attributi personalizzati|Custom definiti attributi per la classe di dominio.<br /><br /> **Nota** usare il pulsante Sfoglia per aggiungere un attributo.|\<nessuno>|
|Nome società|Il nome del nome dell'azienda corrente nel Registro di sistema.|Nome della società corrente|
|nome|Il nome di questa classe di dominio.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi affiliato a questa classe di dominio.|Spazio dei nomi corrente|
|Guid del pacchetto|Il guid per il pacchetto di Visual Studio generato per questo DSL.|\<nessuno>|
|Pacchetto Namespace|Lo spazio dei nomi per il pacchetto di Visual Studio generato per questo DSL.|\<nessuno>|
|Nome prodotto|Il nome del prodotto che verrà registrato per il pacchetto di Visual Studio generato per questo DSL.|\<nessuno>|
|Note|Note associate a questa classe di dominio.|\<nessuno>|
|Descrizione|Descrizione per questa classe di dominio.|\<nessuno>|
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per questa classe di dominio.|\<nessuno>|
|Parola chiave della Guida|La parola chiave della Guida associata a questa classe di dominio.|\<nessuno>|
|Compilazione|Il numero di build incrementali per questa definizione di linguaggio specifico di dominio.|0|
|Numero di versione principale|Il numero di build principale incrementali per questa definizione di linguaggio specifico di dominio.|1|
|Versione secondaria|Il numero di build secondaria incrementali per questa definizione di linguaggio specifico di dominio.|0|
|Revisione|La revisione incrementale numero di build per questa definizione di linguaggio specifico di dominio.|0|

## <a name="see-also"></a>Vedere anche

- [Glossario sugli strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)