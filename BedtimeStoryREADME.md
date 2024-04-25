# ContentView
import SwiftUI

// Define a struct to represent each story
struct Story {
    let title: String
    let summary: String
}

// Define a sample list of stories
let stories = [
    Story(title: "The Moon's Adventure", summary: "Join the Moon in a delightful journey across the starry night."),
    Story(title: "The Whispering Wind", summary: "Listen to the tales of the Wind and its travels around the world."),
    Story(title: "Dreamland Express", summary: "Hop aboard the train that takes you through dreamland."),
    Story(title: "Stars in a Jar", summary: "Discover how a little girl captures the night sky in her little jar.")
]

// Define the SwiftUI view for the ContentView
struct ContentView: View {
    var body: some View {
        NavigationView {
            List(stories, id: \.title) { story in
                HStack {
                    Image(systemName: "star.fill")
                        .foregroundColor(.yellow)
                    VStack(alignment: .leading) {
                        Text(story.title)
                            .font(.headline)
                            .foregroundColor(.primary)
                        Text(story.summary)
                            .font(.subheadline)
                            .foregroundColor(.secondary)
                    }
                }
            }
            .navigationTitle("Bedtime Stories")
            .background(Color.black.opacity(0.8))
            .foregroundColor(.white)
        }
    }
}

// Preview provider for SwiftUI previews in Xcode
struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}

# StoryView

import SwiftUI

struct StoryDetailView: View {
    var story: Story
    
    var body: some View {
        VStack(alignment: .leading, spacing: 20) {
            Spacer(minLength: 20)
            
            Text(story.title)
                .font(.largeTitle)
                .fontWeight(.bold)
                .foregroundColor(.white)
            
            Text(story.summary)
                .font(.title3)
                .foregroundColor(.yellow)
                .multilineTextAlignment(.leading)
                .padding()
            
            Spacer()
        }
        .background(LinearGradient(gradient: Gradient(colors: [ .black, .blue]), startPoint: .top, endPoint: .bottom))
        .edgesIgnoringSafeArea(.all)
    }
}

struct StoryDetailView_Previews: PreviewProvider {
    static var previews: some View {
        StoryDetailView(story: Story(title: "The Whispering Wind", summary: "Listen to the tales of the Wind and its travels around the world."))
    }
}
