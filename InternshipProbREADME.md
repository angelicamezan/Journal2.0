import SwiftUI

struct ContentView: View {
    @State private var numberOfApplications = ""
    @State private var resultText = "Enter the number of applications to calculate the probability."

    var body: some View {
        VStack {
            Spacer()

            Text("Internship Application Probability Calculator")
                .font(.title)
                .fontWeight(.bold)
                .padding()

            TextField("Number of Applications", text: $numberOfApplications)
                .keyboardType(.numberPad)
                .textFieldStyle(RoundedBorderTextFieldStyle())
                .padding()

            Button("Calculate") {
                calculateProbability()
            }
            .foregroundColor(.white)
            .padding()
            .background(Color.blue)
            .cornerRadius(10)

            Text(resultText)
                .font(.callout)
                .padding()
                .multilineTextAlignment(.center)

            Spacer()
        }
        .padding()
    }

    // Function to calculate the probability
    func calculateProbability() {
        guard let applications = Int(numberOfApplications), applications > 0 else {
            resultText = "Please enter a valid, positive number of applications."
            return
        }

        let probabilityPerApplication = 0.05
        let probabilityNone = pow(1 - probabilityPerApplication, Double(applications))
        let probabilityAtLeastOne = 1 - probabilityNone
        let formattedProbability = String(format: "%.2f%%", probabilityAtLeastOne * 100)
        
        resultText = "Probability of getting at least one offer: \(formattedProbability)"
    }
}

struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        ContentView()
    }
}

