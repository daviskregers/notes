# Building a Simple IoC Container

```csharp
namespace SOLID.DIP
{
    class SimpleIoC
    {
        private readonly Dictionary<Type, Type> _map = new Dictionary<Type, Type>();

        public void Register(TFrom, TTo>()
        {
            _map.Add(typeof(TFrom), typeof(TTo));
        }

        public T Resolve<T>()
        {
            return (T)Resolve(typeof(T));
        }

        private object Resolve(Type type)
        {
            Type resolvedType = null;
            try
            {
                resolvedType = _map[type];
            }
            catch
            {
                throw new ArgumentException($"Couldn't resolve type {type}");
            }

            var ctor = resolvedType.GetConstructors().First();
            var ctorParameters = ctor.GetParameters();
            if (ctorParameters.Length == 0)
            {
                return Activator.CreateInstance(resolvedType);
            }

            var parameters = new List<object>();
            foreach (var parameterToResolve in ctorParameters)
            {
                parameters.Add(Resolve(parameterToResolve.ParameterType));
            }

            return ctor.Invoke(parameters.ToArray());
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            SimpleIoC ioc = new SimpleIoC();
            ioc.Register<MainViewModel, MainViewModel>();
            ioc.Register<ICusomer, Customer>();
            ioc.Register<ICustomerRepository, CustomerRepository>();
            ioc.Register<IDbGateway, DbGateway>();

            var mainViewModel = ioc.Resolve<MainViewModel>();
            Console.ReadLine();
        }
    }
}
```
