# Enabling-Microphone #InstallPodsOnTerminal

#ViewController
import UIKit
import InstantSearchVoiceOverlay
class ViewController: UIViewController, VoiceOverlayDelegate {
    
    
    @IBOutlet var appLogo: UIImageView!
    @IBOutlet var mainLabel: UILabel!
    @IBOutlet var userButton: UIButton!
    let voiceOverlay = VoiceOverlayController()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
    }

    @IBAction func welcomeButtonPressed(_ sender: UIButton) {
        voiceOverlay.delegate = self
        voiceOverlay.settings.autoStart = false
        voiceOverlay.settings.autoStop = true
        voiceOverlay.settings.autoStopTimeout = 5
        
        voiceOverlay.start(on: self, textHandler: {text, final, _ in
            if final {
                print("Final text: \(text)")
            }else{
                //print("In Progress: \(text)")
            }
        }, errorHandler: {error in })
    
    
    }
    func recording(text: String?, final: Bool?, error: Error?) {
        
    }
    
}

