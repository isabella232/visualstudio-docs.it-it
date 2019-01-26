---
title: 'CA2210: Gli assembly devono avere nomi sicuri validi'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed9c934c118f70af7cba5e474bd3d777c77c888b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968453"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Gli assembly devono avere nomi sicuri validi

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

### <a name="create-a-key-file"></a>Creare un file di chiave

Usare una delle procedure riportate di seguito:

- Usare lo strumento Assembly Linker (Al.exe) fornito da .NET Framework SDK.

- Per .NET Framework v1.0 o v1.1, usare il <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> o <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> attributo.

- Per il [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], usare il `/keyfile` oppure `/keycontainer` l'opzione del compilatore [/KEYFILE (specificare Key o coppia di chiavi per firmare un Assembly)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) o [/KEYCONTAINER (specifica un contenitore di chiavi per firmare un Assembly)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) opzione del linker in C++).

### <a name="sign-your-assembly-with-a-strong-name-in-visual-studio"></a>Firmare l'assembly con un nome sicuro in Visual Studio

1. In Visual Studio, aprire la soluzione.

2. Nelle **Esplora soluzioni**, fare clic sul progetto e quindi fare clic su **proprietà.**

3. Fare clic sui **Signing** scheda e selezionare il **firmare l'assembly** casella di controllo.

4. Dal **Scegli un file chiave con nome sicuro**, selezionare **New**.

   Il **Crea chiave con nome sicuro** finestra verrà visualizzato.

5. Nelle **nome file di chiave**, digitare un nome per la chiave con nome sicuro.

6. Scegliere se si desidera proteggere la chiave con una password, quindi fare clic su **OK**.

7. Nelle **Esplora soluzioni**, fare clic sul progetto e quindi fare clic su **compilazione**.

### <a name="sign-your-assembly-with-a-strong-name-outside-visual-studio"></a>Firmare l'assembly con nome sicuro all'esterno di Visual Studio

Usare lo strumento nome sicuro (Sn.exe) fornito da .NET Framework SDK. Per altre informazioni, vedere [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Eliminare solo un avviso da questa regola se l'assembly viene usato in un ambiente in cui manomettere il contenuto non è un problema.

## <a name="see-also"></a>Vedere anche

- <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName>
- <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
- [Procedura: Firmare un assembly con un nome sicuro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)
- [Sn.exe (strumento Nome sicuro)](/dotnet/framework/tools/sn-exe-strong-name-tool)