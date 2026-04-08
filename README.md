import React, { useRef } from 'react';
import { Card } from "@/components/ui/card";
import { Separator } from "@/components/ui/separator";
import { RotateCcw } from "lucide-react";
import MedallionScene from '@/components/keychain/MedallionScene';
import DownloadButtons from '@/components/keychain/DownloadButtons';
import DesignInfo from '@/components/keychain/DesignInfo';

export default function KeychainDesigner() {
  const canvasRef = useRef(null);
  const sceneRef = useRef(null);
  const rendererRef = useRef(null);
  const cameraRef = useRef(null);

  return (
    <div className="min-h-screen bg-background">
      {/* Header */}
      <header className="border-b border-border/50 bg-card/80 backdrop-blur-sm sticky top-0 z-10">
        <div className="max-w-6xl mx-auto px-4 sm:px-6 py-4 flex items-center justify-between">
          <div className="flex items-center gap-3">
            <div className="w-8 h-8 rounded-full bg-primary flex items-center justify-center">
              <span className="text-primary-foreground font-heading text-sm font-bold">F</span>
            </div>
            <div>
              <h1 className="font-heading text-xl font-semibold tracking-tight">Medallion Keychain</h1>
              <p className="text-xs text-muted-foreground font-body">3D Preview & Export</p>
            </div>
          </div>
          <div className="flex items-center gap-2 text-xs text-muted-foreground font-body">
            <RotateCcw className="w-3.5 h-3.5" />
            <span className="hidden sm:inline">Drag to rotate</span>
          </div>
        </div>
      </header>

      {/* Main Content */}
      <main className="max-w-6xl mx-auto px-4 sm:px-6 py-8 sm:py-12">
        <div className="grid grid-cols-1 lg:grid-cols-5 gap-8 lg:gap-12">
          {/* 3D Viewer */}
          <div className="lg:col-span-3">
            <Card className="overflow-hidden border-border/50 shadow-xl">
              <div className="aspect-square w-full bg-gradient-to-br from-muted/30 to-muted/60">
                <MedallionScene
                  canvasRef={canvasRef}
                  sceneRef={sceneRef}
                  rendererRef={rendererRef}
                  cameraRef={cameraRef}
                />
              </div>
            </Card>
            <p className="text-center text-xs text-muted-foreground mt-3 font-body">
              Interactive 3D model · Keychain hole included at top
            </p>
          </div>

          {/* Side Panel */}
          <div className="lg:col-span-2 space-y-8">
            {/* Title */}
            <div>
              <h2 className="font-heading text-3xl sm:text-4xl font-bold tracking-tight leading-tight">
                Black Medallion
              </h2>
              <p className="text-muted-foreground font-body mt-2 leading-relaxed">
                Elegant "F" monogram medallion with vine motif, 
                modified with a keychain attachment hole. 
                Ready for 3D printing or digital use.
              </p>
            </div>

            <Separator className="bg-border/50" />

            {/* Specs */}
            <DesignInfo />

            <Separator className="bg-border/50" />

            {/* Downloads */}
            <div className="space-y-4">
              <h3 className="font-heading text-lg font-semibold tracking-wide">Export Files</h3>
              <p className="text-sm text-muted-foreground font-body">
                Download the medallion keychain as a high-resolution PNG image or a 3D-printable STL file.
              </p>
              <DownloadButtons
                rendererRef={rendererRef}
                sceneRef={sceneRef}
                cameraRef={cameraRef}
              />
            </div>

            {/* Original reference */}
            <div className="pt-4">
              <p className="text-xs text-muted-foreground font-body mb-3">Original Design Reference</p>
              <div className="w-20 h-20 rounded-xl overflow-hidden border border-border/50 bg-muted">
                <img
                  src="https://media.base44.com/images/public/user_6885478fe8f1794ddb5f0218/012573210_Blackmedallionwithvinemotif-Picsart-BackgroundRemover.png"
                  alt="Original medallion"
                  className="w-full h-full object-cover"
                />
              </div>
            </div>
          </div>
        </div>
      </main>
    </div>
  );
}
