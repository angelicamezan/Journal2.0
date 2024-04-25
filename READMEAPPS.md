# Journal2.0
# These files include all the work I have done for my journal 2 assigment
# first I'll include the random photo code

//
//  ViewController.swift
//  RandomPhoto
//
//  Created by Angelica Meza on 4/24/24.
//

import UIKit

class ViewController: UIViewController {

    // MARK: - Properties

    // ImageView to display the random photo
    private let imageView: UIImageView = {
        let imageView = UIImageView()
        imageView.contentMode = .scaleAspectFill
        imageView.backgroundColor = .white
        return imageView
    }()
    
    // Button to fetch a new random photo
    private let button: UIButton = {
        let button = UIButton()
        button.backgroundColor = .white
        button.setTitle("RandomPhoto", for: .normal)
        button.setTitleColor(.black, for: .normal)
        return button
    }()
    
    // MARK: - Lifecycle Methods

    override func viewDidLoad() {
        super.viewDidLoad()
        // Set the background color of the view to pink
        view.backgroundColor = .systemPink
        
        // Add image view to the view hierarchy and set its frame
        view.addSubview(imageView)
        imageView.frame = CGRect(x: 0, y: 0, width: 300, height: 300)
        imageView.center = view.center
        
        // Add button to the view hierarchy and set its frame
        view.addSubview(button)
        
        // Fetch a random photo and set up the button's action
        getRandomPhoto()
        button.addTarget(self, action: #selector(didTapButton), for: .touchUpInside)
    }
    
    override func viewDidLayoutSubviews() {
        super.viewDidLayoutSubviews()
        // Set the button's frame relative to the view's frame
        button.frame = CGRect(x: 30, y: view.frame.size.height-150-view.safeAreaInsets.bottom, width: view.frame.size.width-60, height: 55)
    }

    // MARK: - Button Action

    // Method called when the button is tapped
    @objc func didTapButton(){
        getRandomPhoto()
    }

    // MARK: - Helper Methods

    // Method to fetch a random photo from Unsplash and display it in the image view
    func getRandomPhoto() {
        let urlString = "https://source.unsplash.com/random/600x600"
        let url = URL(string: urlString)!
        
        // Attempt to fetch image data from the URL
        guard let data = try? Data(contentsOf: url) else {
            return
        }
        
        // Set the fetched image data to the image view
        imageView.image = UIImage(data:data)
    }
}

# Now here is my ContentBridge Edited Code:

import SwiftUI
extension Color {
    static let navy = Color(red: 0, green: 0, blue: 0.5) // Define navy color
}
struct LoginConfirmationView: View {
    var body: some View {
        VStack(spacing: 20) {
            HStack {
                Image("TopLogo") //made this change because I wanted this page to mimic the frame I had created originally on Canva
                    .resizable()
                    .scaledToFit()
                    .frame(width: 300, height: 100)
                    //.padding(.leading, 20)
                
            }
            //no longer useful because I changed the way it was supposed to look
            //Text("ClientBridge")
               // .font(.largeTitle)
               // .bold()
            
            // Notification/Post UI Component
            ZStack {
                RoundedRectangle(cornerRadius: 10)
                    .fill(Color.white.opacity(0.5))
                    .frame(height: 100)
                    .padding()
                
                Text("This is a mock Business Motivational Quote. ")
                    .padding()
                    .frame(width: 300, height: 100)
                    .background(Color.black.opacity(0.05))
                    .cornerRadius(10)
                    .overlay(
                        RoundedRectangle(cornerRadius: 10)
                            .stroke(Color.navy, lineWidth:6)
                        )
            }
            
            // Make a Post, Past Posts, Invite New Client Buttons
            VStack(spacing: 10) {
                Button("Templates") { }
                .buttonStyle(FilledButton())

                Button("Access Files") { }
                .buttonStyle(FilledButton())

            
            }
            
            Spacer()
            
            // Bottom Icon Buttons
            HStack {
                // Chat Button
                Button(action: {
                    // Future functionality for Chat
                }) {
                    VStack {
                        Image(systemName: "magnifyingglass")
                            .font(.title)
                        Text("Templates")
                            .font(.caption)
                    }
                }
                .foregroundColor(.navy)
                
                Spacer()
                
                // Dash (Home) Button
                Button(action: {
                    // Future functionality for Dash/Home
                }) {
                    VStack {
                        Image(systemName: "house")
                            .font(.title)
                        Text("Dash")
                            .font(.caption)
                    }
                }
                .foregroundColor(.navy)
                
                Spacer()
                
                // Files Button
                Button(action: {
                    // Future functionality for Files
                }) {
                    VStack {
                        Image(systemName: "cloud")
                            .font(.title)
                        Text("Files")
                            .font(.caption)
                    }
                }
                .foregroundColor(.navy)
            }
            .frame(maxWidth: .infinity)
            .padding(.horizontal, 20)
            .padding(.bottom, 20)
        }
        .navigationBarBackButtonHidden(true)
    }
}

// Custom button style for the bottom (trying to follow my design)
struct FilledButton: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        configuration.label
            .foregroundColor(.white)
            .padding()
            .background(Color.navy) // You can adjust this color to navy if you wish
            .cornerRadius(8)
            .scaleEffect(configuration.isPressed ? 0.95 : 1.0)
    }
}

struct LoginConfirmationView_Previews: PreviewProvider {
    static var previews: some View {
        LoginConfirmationView()
    }
}

// 
