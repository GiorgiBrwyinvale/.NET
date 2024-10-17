# .NET


asdoiaonsid


import Combine
import Resolver
import SpaceCore_Domain
import SpaceCore_Network

// MARK: - Protocol
protocol ActivateCardUseCase: UseCase
where Input == CardActivationRequestEntity,
      Output == Void,
      Failure == NetworkError { }

// MARK: - Default Implementation
final class DefaultActivateCardUseCase: ActivateCardUseCase {
    @Injected private var repository: CardActivationRepository

    func execute(
        parameters: CardActivationRequestEntity
    ) -> AnyPublisher<Void, NetworkError> {
        repository.activate(parameters: parameters)
    }
}
```
elenem aricis .NET

```
