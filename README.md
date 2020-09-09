# Basic dependency injection concepts

    import UIKit
    
    protocol APIUserProtocol {
        func request()
    }
    
    class APIUser: APIUserProtocol {
        func request() {
            print("Request: 😎")
        }
        init() {}
        
    }
    
    
    class APIUser {
        func request() {
            print("Request: 😎")
        }
        init() {}
        
    }
    
    
    class ViewController: UIViewController {
        
         private let apiUser: APIUser? = APIUser()
        
        override func viewDidLoad() {
            super.viewDidLoad()
            
        }
        
       required init?(coder: NSCoder) {
           fatalError("init(coder:) has not been implemented")
       }
        
    }
    
    
    class UserViewController: UIViewController {
    
        private let apiUser: APIUser
        
        init(apiUser: APIUser) {
            self.apiUser = apiUser
            super.init(nibName: nil, bundle: nil)
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
        
    }
    
    
    class UserViewController: UIViewController {
    
        private let APIUser: APIUserProtocol
        
        init(APIUser: APIUserProtocol) {
            self.APIUser = APIUser
            super.init(nibName: nil, bundle: nil)
        }
        
        func test() {
            APIUser.request()
        }
        
        required init?(coder: NSCoder) {
            fatalError("init(coder:) has not been implemented")
        }
        
    }
    
    
    let userViewController = UserViewController(APIUser: APIUser())
    
    userViewController.test()
    
