---
title: 'CA2210: Gli assembly devono avere nomi sicuri validi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8b286a67b21d022b12f77ffff68a71da88256757
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095776"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Gli assembly devono avere nomi sicuri validi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Category|Microsoft.Design|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un assembly non è firmato con un nome sicuro, non è stato possibile verificare il nome sicuro, o il nome sicuro non è valido anche senza le impostazioni del Registro di sistema correnti del computer.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola recupera e verifica il nome sicuro di un assembly. Si verifica una violazione se viene soddisfatta una delle operazioni seguenti:

- L'assembly non ha un nome sicuro.

- L'assembly è stato alterato dopo la firma.

- L'assembly è impostata la firma ritardata.

- L'assembly è stato firmato in modo non corretto oppure la firma non è riuscita.

- L'assembly richiede le impostazioni del Registro di sistema superare la verifica. Ad esempio, lo strumento nome sicuro (Sn.exe) è stato usato per ignorare la verifica dell'assembly.

  Il nome sicuro protegge i client dal caricamento involontario di un assembly alterato. Gli assembly con nomi sicuri non devono essere distribuiti al di fuori di scenari molto limitati. Se si condividono o distribuiscono assembly non firmati correttamente, l'assembly può essere alterato, non essere caricato in Common Language Runtime oppure l'utente potrebbe avere la necessità di disabilitare la verifica nel proprio computer. Un assembly senza un nome sicuro ha i seguenti svantaggi:

- Le origini non possono essere verificate.

- Common language runtime non è possibile avvisare gli utenti se il contenuto dell'assembly è stato modificato.

- Non può essere caricato nella global assembly cache.

  Si noti che per caricare e analizzare un assembly con firma ritardata, è necessario disabilitare la verifica dell'assembly.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 **Per creare un file di chiave**

 Usare una delle procedure riportate di seguito:

- Usare lo strumento Assembly Linker (Al.exe) fornito dal [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK.

- Per il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] v1.0 o v1.1, usare il <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> o <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> attributo.

- Per il [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], usare il `/keyfile` oppure `/keycontainer` l'opzione del compilatore [/KEYFILE (specificare Key o coppia di chiavi per firmare un Assembly)](http://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) o [/KEYCONTAINER (specifica un contenitore di chiavi per firmare un Assembly)](http://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) opzione del linker in C++).

  **Per firmare l'assembly con un nome sicuro in Visual Studio**

1. In [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aprire la soluzione.

2. Nelle **Esplora soluzioni**, fare clic sul progetto e quindi fare clic su **proprietà.**

3. Fare clic sui **Signing** scheda e selezionare il **firmare l'assembly** casella di controllo.

4. Dal **Scegli un file chiave con nome sicuro**, selezionare **New**.

    Il **Crea chiave con nome sicuro** finestra verrà visualizzato.

5. Nelle **nome file di chiave**, digitare un nome per la chiave con nome sicuro.

6. Scegliere se si desidera proteggere la chiave con una password, quindi fare clic su **OK**.

7. Nelle **Esplora soluzioni**, fare clic sul progetto e quindi fare clic su **compilazione**.

   **Per firmare l'assembly con nome sicuro all'esterno di Visual Studio**

- Usare lo strumento nome sicuro (Sn.exe) avviene tramite il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] SDK. Per altre informazioni, vedere [Sn.exe (Strong Name Tool)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare solo un avviso da questa regola se l'assembly viene usato in un ambiente in cui manomettere il contenuto non è un problema.

## <a name="see-also"></a>Vedere anche
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Procedura: Firmare un Assembly con nome sicuro](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (strumento nome sicuro)](http://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
