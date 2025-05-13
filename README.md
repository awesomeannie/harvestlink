# harvestlink
import { useState } from "react";
import { Tabs, TabsList, TabsTrigger, TabsContent } from "@/components/ui/tabs";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";

export default function HarvestLinkApp() {
  const [donations, setDonations] = useState([]);
  const [form, setForm] = useState({
    donorName: "",
    foodType: "",
    quantity: "",
    pickupTime: "",
  });

  const handleSubmit = (e) => {
    e.preventDefault();
    setDonations([...donations, form]);
    setForm({ donorName: "", foodType: "", quantity: "", pickupTime: "" });
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-green-50 to-red-50 text-brown-900 font-sans">
      <div className="text-center p-8">
        <h1 className="text-5xl font-bold text-green-800 mb-2">HarvestLink</h1>
        <p className="text-xl text-brown-700">
          Fighting hunger with technology and community.
        </p>
      </div>

      <Tabs defaultValue="dashboard" className="max-w-4xl mx-auto p-4">
        <TabsList className="grid grid-cols-6 gap-2">
          <TabsTrigger value="dashboard">Dashboard</TabsTrigger>
          <TabsTrigger value="donate">Donate Food</TabsTrigger>
          <TabsTrigger value="reports">Reports</TabsTrigger>
          <TabsTrigger value="about">About Us</TabsTrigger>
          <TabsTrigger value="revenue">Revenue</TabsTrigger>
          <TabsTrigger value="team">Team</TabsTrigger>
        </TabsList>

        <TabsContent value="dashboard">
          <Card>
            <CardContent className="p-6 space-y-4">
              <h2 className="text-2xl font-semibold text-green-800">Live Donations</h2>
              {donations.length === 0 ? (
                <p>No donations yet. Be the first to contribute!</p>
              ) : (
                <ul className="list-disc pl-6">
                  {donations.map((d, index) => (
                    <li key={index}>
                      <strong>{d.donorName}</strong> donated {d.quantity} of {d.foodType} (Pickup: {d.pickupTime})
                    </li>
                  ))}
                </ul>
              )}
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="donate">
          <Card>
            <CardContent className="p-6 space-y-4">
              <h2 className="text-2xl font-semibold text-green-800">Donate Surplus Food</h2>
              <form onSubmit={handleSubmit} className="space-y-4">
                <Input
                  placeholder="Donor Name"
                  value={form.donorName}
                  onChange={(e) => setForm({ ...form, donorName: e.target.value })}
                  required
                />
                <Input
                  placeholder="Food Type"
                  value={form.foodType}
                  onChange={(e) => setForm({ ...form, foodType: e.target.value })}
                  required
                />
                <Input
                  placeholder="Quantity"
                  value={form.quantity}
                  onChange={(e) => setForm({ ...form, quantity: e.target.value })}
                  required
                />
                <Input
                  placeholder="Pickup Time"
                  value={form.pickupTime}
                  onChange={(e) => setForm({ ...form, pickupTime: e.target.value })}
                  required
                />
                <Button type="submit" className="bg-green-700 hover:bg-green-800">Submit Donation</Button>
              </form>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="reports">
          <Card>
            <CardContent className="p-6 space-y-4">
              <h2 className="text-2xl font-semibold text-green-800">Donation Reports</h2>
              <p>Our premium plan users receive automated tax and impact reports including meals saved and emissions reduced.</p>
              <p>
                Features included:
                <ul className="list-disc pl-6">
                  <li>Real-time tracking of donations</li>
                  <li>Impact visualization</li>
                  <li>Pickup scheduling and volunteer coordination</li>
                </ul>
              </p>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="revenue">
          <Card>
            <CardContent className="p-6 space-y-4">
              <h2 className="text-2xl font-semibold text-green-800">Revenue Model</h2>
              <ul className="list-disc pl-6">
                <li>Freemium subscription system for users</li>
                <li>Free Plan: small nonprofits and donors</li>
                <li>Premium Plan ($2,000/year): includes logistics optimization, analytics, early access to features, and more</li>
                <li>Additional revenue from corporate sponsorships, grant funding, and donations</li>
              </ul>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="about">
          <Card>
            <CardContent className="p-6 space-y-4">
              <h2 className="text-2xl font-semibold text-green-800">About Us</h2>
              <p>
                HarvestLink bridges the gap between food donors and recipients using innovative technology and local collaboration.
              </p>
              <p>
                Visit our website: <a href="https://annikajain22.wixsite.com/harvestlink" className="text-green-700 underline" target="_blank">HarvestLink Website</a>
              </p>
              <p>
                Contact Us: <br/>
                📧 Annika: <a href="mailto:annikajain22@gmail.com" className="text-red-700">annikajain22@gmail.com</a><br/>
                📧 Rebecca: <a href="mailto:rebetoch@gmail.com" className="text-red-700">rebetoch@gmail.com</a>
              </p>
            </CardContent>
          </Card>
        </TabsContent>

        <TabsContent value="team">
          <Card>
            <CardContent className="p-6 space-y-4">
              <h2 className="text-2xl font-semibold text-green-800">Meet the Team</h2>
              <p>
                <strong>Annika Jain – CEO:</strong> Manages finances and major team meetings necessary to ensure the success of the business. She also helps guide the overall vision and strategy of HarvestLink to keep the team aligned toward their goals.
              </p>
              <p>
                <strong>Rebecca Tochilnikov – COO:</strong> Manages smaller but necessary team meetings and all employees to ensure success and collaboration across all departments. She also oversees day-to-day operations to make sure the team's work stays efficient and organized.
              </p>
            </CardContent>
          </Card>
        </TabsContent>
      </Tabs>
    </div>
  );
}
